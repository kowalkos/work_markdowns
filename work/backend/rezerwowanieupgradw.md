---
id: rezerwowanieupgradw
aliases:
  - RezerwowanieUpgradów
tags: []
---

# RezerwowanieUpgradów

1. na Release perspectiv utworzyć pusty upgrade

```cs
    [UpgradeClass(UpgradeNumber = 296, Enabled = false)]
    internal class Upgrade00296 : PerspectivUpgrade
    {
        public override void Execute()
        {
            // rezerwacja {imie nazwisko -> pierwsze litery} {numer zadania }
        }
    }
```

2. tworzony comit z wiadomością "rezerwacja upgrade'u" na Release
   Wiadomość nie może mieć oznaczenia numeru zadania ani imienia audytora
