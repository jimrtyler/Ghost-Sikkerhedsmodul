# 👻 Ghost Security Modul
**PowerShell-Baseret Windows & Azure Sikkerhedshærdning**

> **Proaktiv sikkerhedshærdning til Windows-slutpunkter og Azure-miljøer.** Ghost leverer PowerShell-baserede hærdningsfunktioner, der kan hjælpe med at reducere almindelige angrebsvektorer ved at deaktivere unødvendige tjenester og protokoller.

## ⚠️ Vigtige Ansvarsfraskrivelser

**TEST KRÆVET**: Test altid Ghost i ikke-produktionsmiljøer først. Deaktivering af tjenester kan påvirke legitime forretningsfunktioner.

**INGEN GARANTIER**: Selvom Ghost målretter almindelige angrebsvektorer, kan intet sikkerhedsværktøj forhindre alle angreb. Dette er en komponent i en omfattende sikkerhedsstrategi.

**OPERATIONEL PÅVIRKNING**: Nogle funktioner kan påvirke systemfunktionalitet. Gennemgå hver indstilling omhyggeligt før implementering.

**PROFESSIONEL VURDERING**: For produktionsmiljøer, konsulter sikkerhedsprofessionelle for at sikre, at indstillinger stemmer overens med din organisations behov.

## 📊 Sikkerhedslandskabet

Ransomware-skader nåede **57 milliarder dollars i 2025**, og forskning viser, at mange succesfulde angreb udnytter grundlæggende Windows-tjenester og fejlkonfigurationer. Almindelige angrebsvektorer inkluderer:

- **90% af ransomware-hændelser** involverer RDP-udnyttelse
- **SMBv1-sårbarheder** muliggjorde angreb som WannaCry og NotPetya
- **Dokumentmakroer** forbliver en primær malware-leveringsmetode
- **USB-baserede angreb** fortsætter med at målrette luft-gappede netværk
- **PowerShell-misbrug** er steget betydeligt i de seneste år

## 🛡️ Ghost Sikkerhedsfunktioner

Ghost leverer **16 Windows-hærdningsfunktioner** plus **Azure-sikkerhedsintegration**:

### Windows Slutpunkt-hærdning

| Funktion | Formål | Overvejelser |
|----------|--------|--------------|
| `Set-RDP` | Administrerer Remote Desktop-adgang | Kan påvirke fjernadministration |
| `Set-SMBv1` | Kontrollerer legacy SMB-protokol | Kræves til meget gamle systemer |
| `Set-AutoRun` | Kontrollerer AutoPlay/AutoRun | Kan påvirke brugerbekvemmelighed |
| `Set-USBStorage` | Begrænser USB-lagerenheder | Kan påvirke legitim USB-brug |
| `Set-Macros` | Kontrollerer Office-makroeksekvering | Kan påvirke makro-aktiverede dokumenter |
| `Set-PSRemoting` | Administrerer PowerShell-fjernkommunikation | Kan påvirke fjernstyring |
| `Set-WinRM` | Kontrollerer Windows Remote Management | Kan påvirke fjernadministration |
| `Set-LLMNR` | Administrerer navneopløsningsprotokol | Normalt sikkert at deaktivere |
| `Set-NetBIOS` | Kontrollerer NetBIOS over TCP/IP | Kan påvirke legacy-applikationer |
| `Set-AdminShares` | Administrerer administrative shares | Kan påvirke fjernfiladgang |
| `Set-Telemetry` | Kontrollerer dataindsamling | Kan påvirke diagnostiske kapaciteter |
| `Set-GuestAccount` | Administrerer gæstekonto | Normalt sikkert at deaktivere |
| `Set-ICMP` | Kontrollerer ping-svar | Kan påvirke netværksdiagnostik |
| `Set-RemoteAssistance` | Administrerer fjernhjælp | Kan påvirke helpdesk-operationer |
| `Set-NetworkDiscovery` | Kontrollerer netværksopdagelse | Kan påvirke netværksbrowsing |
| `Set-Firewall` | Administrerer Windows Firewall | Kritisk for netværkssikkerhed |

### Azure Cloud Sikkerhed

| Funktion | Formål | Krav |
|----------|--------|------|
| `Set-AzureSecurityDefaults` | Aktiverer grundlæggende Azure AD-sikkerhed | Microsoft Graph-tilladelser |
| `Set-AzureConditionalAccess` | Konfigurerer adgangspolitikker | Azure AD P1/P2-licenser |
| `Set-AzurePrivilegedUsers` | Auditerer privilegerede konti | Global Admin-tilladelser |

### Virksomhedsimplementeringsmuligheder

| Metode | Anvendelse | Krav |
|--------|------------|------|
| **Direkte Eksekvering** | Test, små miljøer | Lokale admin-rettigheder |
| **Group Policy** | Domænemiljøer | Domæneadmin, GP-styring |
| **Microsoft Intune** | Cloud-administrerede enheder | Intune-licenser, Graph API |

## 🚀 Hurtig Start

### Sikkerhedsvurdering
```powershell
# Indlæs Ghost-modul
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Tjek nuværende sikkerhedsstilling
Get-Ghost
```

### Grundlæggende Hærdning (Test Først)
```powershell
# Essentiel hærdning - test i laboratoriemiljø først
Set-Ghost -SMBv1 -AutoRun -Macros

# Gennemgå ændringer
Get-Ghost
```

### Virksomhedsimplementering
```powershell
# Group Policy-implementering (domænemiljøer)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune-implementering (cloud-administrerede enheder)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Installationsmetoder

### Mulighed 1: Direkte Download (Test)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Mulighed 2: Modulinstallation
```powershell
# Installer fra PowerShell Gallery (når tilgængelig)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Mulighed 3: Virksomhedsimplementering
```powershell
# Kopier til netværksplacering for Group Policy-implementering
# Konfigurer Intune PowerShell-scripts til cloud-implementering
```

## 💼 Anvendelseseksempler

### Lille Virksomhed
```powershell
# Grundlæggende beskyttelse med minimal påvirkning
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Sundhedsmiljø
```powershell
# HIPAA-fokuseret hærdning
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Finansielle Tjenester
```powershell
# Højsikkerhedskonfiguration
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Cloud-Først Organisation
```powershell
# Intune-administreret implementering
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 📝 Funktionsdetaljer

### Kernehærdningsfunktioner

#### Netværkstjenester
- **RDP**: Blokerer fjernskrivebordsadgang eller randomiserer port
- **SMBv1**: Deaktiverer legacy fildelingsprotokol
- **ICMP**: Forhindrer ping-svar til rekognoscering
- **LLMNR/NetBIOS**: Blokerer legacy navneopløsningsprotokoller

#### Applikationssikkerhed
- **Makroer**: Deaktiverer makroeksekvering i Office-applikationer
- **AutoRun**: Forhindrer automatisk eksekvering fra flyttbare medier

#### Fjernstyring
- **PSRemoting**: Deaktiverer PowerShell-fjernsessioner
- **WinRM**: Stopper Windows Remote Management
- **Fjernhjælp**: Blokerer fjernhjælpsforbindelser

#### Adgangskontrol
- **Admin Shares**: Deaktiverer C$, ADMIN$ shares
- **Gæstekonto**: Deaktiverer gæstekonti-adgang
- **USB-lager**: Begrænser USB-enhedsbrug

### Azure Integration
```powershell
# Forbind til Azure-tenant
Connect-AzureGhost -Interactive

# Aktiver sikkerhedsstandarder
Set-AzureSecurityDefaults -Enable

# Konfigurer betinget adgang
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Auditer privilegerede brugere
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune Integration (Nyt i v2)
```powershell
# Forbind til Intune
Connect-IntuneGhost -Interactive

# Implementer via Intune-politikker
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Vigtige Overvejelser

### Testkrav
- **Laboratoriemiljø**: Test alle indstillinger i isoleret miljø først
- **Fasevis Implementering**: Udrulning gradvist for at identificere problemer
- **Tilbagerulningsplan**: Sørg for at kunne vende ændringer om hvis nødvendigt
- **Dokumentation**: Registrer hvilke indstillinger virker for dit miljø

### Potentiel Påvirkning
- **Brugerproduktivitet**: Nogle indstillinger kan påvirke daglige arbejdsgange
- **Legacy-applikationer**: Ældre systemer kan kræve bestemte protokoller
- **Fjernadgang**: Overvej påvirkning på legitim fjernadministration
- **Forretningsprocesser**: Verificer at indstillinger ikke ødelægger kritiske funktioner

### Sikkerhedsbegrænsninger
- **Forsvar i Dybden**: Ghost er et lag af sikkerhed, ikke en komplet løsning
- **Løbende Styring**: Sikkerhed kræver kontinuerlig overvågning og opdateringer
- **Brugertræning**: Tekniske kontrolfunktioner skal parres med sikkerhedsbevidsthed
- **Trusselevolution**: Nye angrebsmetoder kan omgå nuværende beskyttelse

## 🎯 Eksempel Angrebsscenarier

Selvom Ghost målretter almindelige angrebsvektorer, afhænger specifik forebyggelse af korrekt implementering og test:

### WannaCry-Lignende Angreb
- **Afbødning**: `Set-Ghost -SMBv1` deaktiverer den sårbare protokol
- **Overvejelse**: Sørg for at ingen legacy-systemer kræver SMBv1

### RDP-Baseret Ransomware
- **Afbødning**: `Set-Ghost -RDP` blokerer fjernskrivebordsadgang
- **Overvejelse**: Kan kræve alternative fjernadgangsmetoder

### Dokument-Baseret Malware
- **Afbødning**: `Set-Ghost -Macros` deaktiverer makroeksekvering
- **Overvejelse**: Kan påvirke legitime makro-aktiverede dokumenter

### USB-Leverede Trusler
- **Afbødning**: `Set-Ghost -USBStorage -AutoRun` begrænser USB-funktionalitet
- **Overvejelse**: Kan påvirke legitim USB-enhedsbrug

## 🏢 Virksomhedsfunktioner

### Group Policy Support
```powershell
# Anvend indstillinger via Group Policy-register
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Indstillinger anvendes domæne-bredt efter GP-opdatering
gpupdate /force
```

### Microsoft Intune Integration
```powershell
# Opret Intune-politikker for Ghost-indstillinger
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Politikker implementeres automatisk til administrerede enheder
```

### Compliance Rapportering
```powershell
# Generer sikkerhedsvurderingsrapport
Get-Ghost | Export-Csv -Path "SikkerhedsAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure sikkerhedsstillingsrapport
Get-AzureGhost | Out-File "AzureSikkerhedsRapport.txt"
```

## 📚 Bedste Praksis

### Før Implementering
1. **Dokumenter Nuværende Tilstand**: Kør `Get-Ghost` før ændringer
2. **Test Grundigt**: Valider i ikke-produktionsmiljø
3. **Planlæg Tilbagerulning**: Vid hvordan man vender hver indstilling om
4. **Interessent Gennemgang**: Sørg for at forretningsenheder godkender ændringer

### Under Implementering
1. **Fasevis Tilgang**: Implementer til pilotgrupper først
2. **Overvåg Påvirkning**: Hold øje med brugerklager eller systemproblemer
3. **Dokumenter Problemer**: Registrer eventuelle problemer til fremtidig reference
4. **Kommuniker Ændringer**: Informer brugere om sikkerhedsforbedringer

### Efter Implementering
1. **Regelmæssig Vurdering**: Kør periodisk `Get-Ghost` for at verificere indstillinger
2. **Opdater Dokumentation**: Hold sikkerhedskonfigurationer aktuelle
3. **Gennemgå Effektivitet**: Overvåg for sikkerhedshændelser
4. **Kontinuerlig Forbedring**: Juster indstillinger baseret på trussellandskab

## 🔧 Fejlfinding

### Almindelige Problemer
- **Tilladelsesfel**: Sørg for forhøjet PowerShell-session
- **Tjenesteafhængigheder**: Nogle tjenester kan have afhængigheder
- **Applikationskompatibilitet**: Test med forretningsapplikationer
- **Netværksforbindelse**: Verificer at fjernadgang stadig virker

### Gendannelsesmuligheder
```powershell
# Genaktiver specifikke tjenester hvis nødvendigt
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Om Forfatteren

**Jim Tyler** - Microsoft MVP for PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10.000+ abonnenter)
- **Nyhedsbrev**: [PowerShell.News](https://powershell.news) - Ugentlig sikkerhedsintelligens
- **Forfatter**: "PowerShell for Systems Engineers"
- **Erfaring**: Årtier med PowerShell-automatisering og Windows-sikkerhed

## 📄 Licens & Ansvarsfraskrivelse

### MIT Licens
Ghost leveres under MIT-licensen til fri brug, ændring og distribution.

### Sikkerhedsansvarsfraskrivelse
- **Ingen Garanti**: Ghost leveres "som den er" uden garanti af nogen art
- **Test Krævet**: Test altid i ikke-produktionsmiljøer først
- **Professionel Vejledning**: Konsulter sikkerhedsprofessionelle for produktionsimplementeringer
- **Operationel Påvirkning**: Forfatterne er ikke ansvarlige for operationelle forstyrrelser
- **Omfattende Sikkerhed**: Ghost er en komponent i en komplet sikkerhedsstrategi

### Support
- **GitHub Issues**: [Rapporter fejl eller anmod om funktioner](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentation**: Brug `Get-Help <funktion> -Full` for detaljeret hjælp
- **Fællesskab**: PowerShell og sikkerhedsfællesskabsforummer

---

**🔒 Styrk din sikkerhedsstilling med Ghost - men test altid først.**

```powershell
# Start med vurdering, ikke antagelser
Get-Ghost
```

**⭐ Stjern dette repository hvis Ghost hjælper med at forbedre din sikkerhedsstilling!**