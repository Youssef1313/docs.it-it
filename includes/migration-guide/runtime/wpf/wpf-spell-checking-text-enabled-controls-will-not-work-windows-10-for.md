---
ms.openlocfilehash: 97ca78e154eb25e863256e06caa119fe753bc344
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858655"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>Il controllo ortografico WPF nei controlli con supporto di testo non funziona in Windows 10 per le lingue non incluse nell'elenco lingue di input del sistema operativo

|   |   |
|---|---|
|Dettagli|Durante l'esecuzione in Windows 10, il controllo ortografico potrebbe non funzionare per i controlli WPF basati su testo perché le funzionalità di controllo ortografico della piattaforma sono disponibili solo per le lingue presenti nell'elenco delle lingue di input. In Windows 10, quando una lingua viene aggiunta all'elenco di tastiere disponibili, Windows scarica e installa automaticamente una funzione corrispondente nel pacchetto di funzionalità su richiesta (FOD, Feature on Demand) che offre funzionalità di controllo ortografico. Aggiungendo la lingua all'elenco di lingue di input, il controllo ortografico sarà supportato.|
|Suggerimento|Tenere presente che per il funzionamento del controllo ortografico in Windows 10 è necessario aggiungere la lingua o il testo da sottoporre a controllo come lingua di input.|
|Ambito|Microsoft Edge|
|Versione|4.6|
|Tipo|Runtime|

