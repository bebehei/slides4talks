# About Me
# Who are we
  - B2B Video Hosting
  - Vimeo && DSGVO
  - ~PB Ceph HDD Cluster mit Videos 
  - Transcoding-Cluster für VoD-Ingest
  - RTMP/SRT-Ingest für Livesignale
  - Eigenes europ. CDN für Video-Auslieferung
  - Sonst: Webshop-IT (LNMP-Stack)
  - Bis: 2024 ausschliesslich bei 

# Pläne
  - Colocation reduziert Kosten
  - Oh Fuck, es gibt auch noch Sovereignty

# Netzwerk Architektur im Rack

Vorheriger Arbeitgeber:

- Viele Standorte, meisst Single-Rack
- L2 nur im selben Rack
- Server hat Bond aus Primary/Backup
- 1x Primary Switch (bspw. QFX5120-32C)
- 1x Backup Switch (bspw. EX4300-48MP)

Ziel jetzt:

- Viele Standorte, meisst Single-Rack
- Alles Layer3
- 2x Primary Switch (bspw. QFX5120-32C)
- Jeder Server hat ein Interface zu jedem Switch
    - Bond aus MLAG/EVPN-MH
    - BGP Layer 3

Cherry-on-top: IaC ist kein Pain in the Ass

# Welche Möglichkeiten gibt's?

## Klassische Hersteller

- Good: Support
- Bad: Preis
- Bekannt: Juniper
- Unbekannt: Alles andere

- 1x QFX5120-32C refurbished + 3 Jahre Lizenz: 20K EUR

Vermutung: Cisco ähnlicher Preis, Arista etwas günstiger

-> Wir haben 20K Benchmark. Geht es besser und/oder günstiger?

## SONiC / Switch Abstraction Interface

- "Software for Open Networking in the Cloud"
- Open Source, Entwicklung auf GitHub: https://sonicfoundation.dev/
- Kommunikation OS <-> ASIC basiert auf SAI (Switch Abstraction Interface)
- Funktioniert auf vielen Switches
    - Accton
    - Arista
    - Dell 
    - Supermicro
    - *uvm* ...
    - https://sonic-net.github.io/SONiC/Supported-Devices-and-Platforms.html
- Sehr gut: Containerlab-Support
    -> Bootstrapping und tests easy

Features:

- MLAG funktioniert (?!)
   - HLD existiert, Konfigurationsoptionen fehlen?
- EVPN unsupported
- BGP: FRR (meh!)

### Zustand SONiC

- Images
  - Links auf https://sonic-net.github.io/SONiC/Supported-Devices-and-Platforms.html alle tot:
    - Team Foundation Fehler: BuildNotFoundException
  - Containerlab beschreibt es am besten:
    - Sonic.software -- an unofficial repo with SONiC images (may be down sometimes, uses Azure pipeline as a source)
    - Azure pipeline -- an official source of SONiC images, but finding the right one there is a pita
