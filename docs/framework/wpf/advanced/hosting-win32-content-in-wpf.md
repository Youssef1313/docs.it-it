---
title: Hosting di contenuto Win32 in WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 3b6e30a612c87880121c227c85c4bd6a7ef31f40
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920238"
---
# <a name="hosting-win32-content-in-wpf"></a>Hosting di contenuto Win32 in WPF

## <a name="prerequisites"></a>Prerequisites

Vedere l' [interoperatività di WPF e Win32](wpf-and-win32-interoperation.md).

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Procedura dettagliata di Win32 all'interno di Windows Presentation Framework (HwndHost)

Per riutilizzare [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contenuto all'interno di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazioni, utilizzare <xref:System.Windows.Interop.HwndHost>, ovvero un controllo che rende gli HWND simili a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenuto. Come <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> è semplice da usare: derivare da <xref:System.Windows.Interop.HwndHost> e implementare i metodi `BuildWindowCore` e `DestroyWindowCore`, quindi creare un'istanza della classe derivata <xref:System.Windows.Interop.HwndHost> e inserirla all'interno dell'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Se la logica di [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] è già inclusa nel pacchetto come controllo, l'implementazione del `BuildWindowCore` è poco più di una chiamata a `CreateWindow`. Ad esempio, per creare un controllo LISTBOX [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] in C++:

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

Ma si supponga che il codice [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] non sia così indipendente? In tal caso, è possibile creare una finestra di dialogo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e incorporarne il contenuto in un'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] più grande. L'esempio mostra questo aspetto in Visual Studio C++e, sebbene sia anche possibile eseguire questa operazione in un linguaggio diverso o nella riga di comando.

Iniziare con una semplice finestra di dialogo, compilata C++ in un progetto DLL.

Successivamente, introdurre la finestra di dialogo nell'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] più grande:

- Compila la DLL come gestita (`/clr`)

- Trasformare la finestra di dialogo in un controllo

- Definire la classe derivata di <xref:System.Windows.Interop.HwndHost> con i metodi `BuildWindowCore` e `DestroyWindowCore`

- Eseguire l'override del metodo `TranslateAccelerator` per gestire le chiavi di dialogo

- Eseguire l'override del metodo `TabInto` per supportare la tabulazione

- Eseguire l'override `OnMnemonic` metodo per supportare i tasti di scelta

- Creare un'istanza della sottoclasse <xref:System.Windows.Interop.HwndHost> e inserirla nell'elemento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] corretto

### <a name="turn-the-dialog-into-a-control"></a>Trasformare la finestra di dialogo in un controllo

È possibile trasformare una finestra di dialogo in un HWND figlio utilizzando gli stili WS_CHILD e DS_CONTROL. Passare al file di risorse (. RC) in cui è definita la finestra di dialogo e trovare l'inizio della definizione della finestra di dialogo:

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

Modificare la seconda riga in:

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Questa azione non esegue completamente il pacchetto in un controllo indipendente; è comunque necessario chiamare `IsDialogMessage()` in modo che [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] possa elaborare determinati messaggi, ma la modifica del controllo fornisce un modo semplice per inserire i controlli all'interno di un altro HWND.

## <a name="subclass-hwndhost"></a>Classe HwndHost

Importare gli spazi dei nomi seguenti:

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

Creare quindi una classe derivata di <xref:System.Windows.Interop.HwndHost> ed eseguire l'override dei metodi `BuildWindowCore` e `DestroyWindowCore`:

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

Qui si usa il `CreateDialog` per creare la finestra di dialogo che è effettivamente un controllo. Poiché si tratta di uno dei primi metodi chiamati all'interno della DLL, è necessario eseguire alcune operazioni di inizializzazione [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] standard chiamando una funzione che verrà definita in seguito, denominata `InitializeGlobals()`:

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Eseguire l'override del metodo TranslateAccelerator per gestire le chiavi di dialogo

Se è stato eseguito questo esempio, si otterrebbe un controllo finestra di dialogo che viene visualizzato, ma si ignorerà tutta l'elaborazione della tastiera che rende una finestra di dialogo funzionante. A questo punto, è necessario eseguire l'override dell'implementazione di `TranslateAccelerator` (che deriva da `IKeyboardInputSink`, un'interfaccia che <xref:System.Windows.Interop.HwndHost> implementa). Questo metodo viene chiamato quando l'applicazione riceve WM_KEYDOWN e WM_SYSKEYDOWN.

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

Si tratta di una grande quantità di codice in un pezzo, quindi è possibile usare alcune spiegazioni più dettagliate. Per prima cosa, il C++ codice C++ usa le macro e; è necessario tenere presente che esiste già una macro denominata`TranslateAccelerator`, definita in winuser. h:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Assicurarsi quindi di definire un metodo di `TranslateAccelerator` e non un metodo di `TranslateAcceleratorW`.

Analogamente, sono presenti sia il messaggio winuser. h non gestito che lo struct `Microsoft::Win32::MSG` gestito. È possibile evitare ambiguità tra le due utilizzando l' C++ operatore`::`.

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

Tornare a `TranslateAccelerator`. Il principio di base consiste nel chiamare la funzione [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] `IsDialogMessage` per eseguire il maggior lavoro possibile, ma `IsDialogMessage` non ha accesso ad alcun elemento all'esterno della finestra di dialogo. Come scheda utente intorno alla finestra di dialogo, quando la tabulazione viene eseguita oltre l'ultimo controllo nella finestra di dialogo, è necessario impostare lo stato attivo sulla parte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chiamando `IKeyboardInputSite::OnNoMoreStops`.

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

Infine, viene chiamato `IsDialogMessage`. Tuttavia, una delle responsabilità di un metodo di `TranslateAccelerator` indica [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se la sequenza di tasti è stata gestita o meno. Se non è stato gestito, l'evento di input può eseguire il tunneling e la bolla nel resto dell'applicazione. In questo caso si esporrà una peculiarità della gestione questo caso della tastiera e della natura dell'architettura di input in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Sfortunatamente, `IsDialogMessage` non restituisce alcun modo se gestisce una particolare sequenza di tasti. Ancora peggio, chiamerà `DispatchMessage()` sulle sequenze di tasti che non devono essere gestite.  Sarà quindi necessario decompilare `IsDialogMessage`e chiamarlo solo per le chiavi che si sa gestire:

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a>Eseguire l'override del metodo TabInto per supportare la tabulazione

Ora che è stata implementata `TranslateAccelerator`, un utente può spostarsi all'interno della finestra di dialogo e visualizzarne la scheda in un'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] maggiore. Tuttavia, un utente non può riportare la scheda nella finestra di dialogo. Per risolvere il problemi, è necessario eseguire l'override di `TabInto`:

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

Il parametro `TraversalRequest` indica se l'azione della scheda è una scheda o una scheda di spostamento.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Eseguire l'override del metodo onmnemonico per supportare i tasti di scelta

La gestione della tastiera è quasi completa, ma manca un elemento: i tasti di scelta non funzionano. Se un utente preme ALT + F, lo stato attivo non passa alla casella di modifica "First Name:". Quindi, si esegue l'override del metodo `OnMnemonic`:

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

Perché non chiamare `IsDialogMessage` qui?  Si ha lo stesso problema di prima: è necessario essere in grado di informare [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] codice se il codice ha gestito o meno la sequenza di tasti e `IsDialogMessage` non è possibile eseguire questa operazione. Esiste anche un secondo problema, perché `IsDialogMessage` rifiuta di elaborare il tasto di scelta se l'HWND con stato attivo non si trova all'interno della finestra di dialogo.

### <a name="instantiate-the-hwndhost-derived-class"></a>Creare un'istanza della classe derivata HwndHost

Infine, ora che tutto il supporto per chiavi e schede è disponibile, è possibile inserire il <xref:System.Windows.Interop.HwndHost> nell'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] più grande. Se l'applicazione principale viene scritta in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], il modo più semplice per inserirlo nella posizione corretta consiste nel lasciare un elemento <xref:System.Windows.Controls.Border> vuoto in cui si desidera inserire il <xref:System.Windows.Interop.HwndHost>. Qui viene creato un <xref:System.Windows.Controls.Border> denominato `insertHwndHostHere`:

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

Quindi, tutto ciò che rimane è trovare un posto valido nella sequenza di codice per creare un'istanza del <xref:System.Windows.Interop.HwndHost> e connetterlo al <xref:System.Windows.Controls.Border>. In questo esempio, verrà inserito nel costruttore per la classe derivata <xref:System.Windows.Window>:

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

Che offre:

![Screenshot dell'app WPF in esecuzione.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>Vedere anche

- [Interoperatività di WPF e Win32](wpf-and-win32-interoperation.md)
