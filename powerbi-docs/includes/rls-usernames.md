---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "61194082"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Uso della funzione DAX username() o userprincipalname()
È possibile sfruttare la funzione DAX *username()* o *userprincipalname()* all'interno del set di dati. Queste funzioni possono essere usate all'interno di espressioni in Power BI Desktop. Quando si pubblica il modello, verrà usata all'interno del servizio Power BI.

All'interno di Power BI Desktop, *username()* restituirà un utente nel formato *DOMINIO\utente*, mentre *userprincipalname()* restituirà un utente nel formato <em>user@contoso.com</em>.

All'interno del servizio Power BI, *username()* e *userprincipalname()* restituiranno il nome dell'entità utente (UPN, User Principal Name). simile a un indirizzo di posta elettronica.

