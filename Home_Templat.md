
# Projektbeschreibung

**Projektname:** Internal Developer Platform (Platform Engineering Initiative)

**Beschreibung:**

Dieses Projekt implementiert eine vollständige **Internal Developer Platform (IDP)** auf Basis von **Backstage**, um Entwicklerteams Self-Service-Funktionen, Transparenz und standardisierte Entwicklungsprozesse bereitzustellen.

Ziel des Projekts ist es, eine zentrale Plattform zu schaffen, die Services, Dokumentation, CI/CD, Kubernetes-Workloads und GitOps-Deployments an einem Ort vereint. Entwickler können neue Projekte über sogenannte *Golden Path Templates* erstellen, Deployments verfolgen und ihre Services inklusive Dokumentation eigenständig verwalten.

Die Motivation hinter diesem Projekt ist die Reduzierung von kognitiver Last, die Standardisierung von Entwicklungsprozessen sowie die Beschleunigung von Onboarding und Delivery-Zyklen.

**Was Benutzer erwarten können:**

* Zentrales Developer Portal mit Software-Katalog
* Self-Service-Projekterstellung mit CI/CD
* Kubernetes-Workload-Transparenz
* GitOps-Integration
* Dokumentation-as-Code
* Single Sign-On mit rollenbasierter Zugriffskontrolle
* Produktionsnahe Setup-Struktur (lokal, Docker, Kubernetes)

---

## Technologien und Werkzeuge

Die folgenden Technologien und Tools wurden im Projekt eingesetzt:

### Core Platform

* **Backstage** – Developer Portal Framework
* **TypeScript** – Plugin- und Backend-Entwicklung
* **Node.js** – Backend Runtime
* **React** – Frontend & Plugin-Entwicklung

### Container & Deployment

* **Docker** – Containerisierung (Multi-Stage Builds)
* **Kubernetes** – Orchestrierung & Workload-Management
* **GitHub Container Registry** – Image Storage
* **Argo CD** – GitOps Deployment Visibility

### CI/CD & SCM

* **GitHub** – Source Control & Repository Discovery
* **GitHub Actions** – CI/CD Pipelines

### Authentifizierung & Sicherheit

* **Keycloak** – OIDC Authentication & SSO

### Dokumentation

* **TechDocs** – Documentation-as-Code
* **MkDocs** – Dokumentationsgenerierung

---

## Hauptmerkmale

### 1️⃣ Vollständiger Software Catalog

* Verwaltung von Services, APIs, Teams und Systemen
* Automatische GitHub Repository Discovery
* Katalog-Validierung & Troubleshooting

### 2️⃣ Golden Path Software Templates

* Vordefinierte Produktions-Templates
* Automatische Erstellung von Repositories
* CI/CD Pipeline inklusive Container-Build & Deployment
* GitHub Actions Workflows mit sicheren Registry-Permissions

### 3️⃣ Kubernetes & Workload Visibility

* Kubernetes Plugin Konfiguration
* Mapping von Catalog-Entities zu Kubernetes Ressourcen via Annotation
* Namespace-Isolation für Multi-Tenant-Cluster

### 4️⃣ GitOps Integration

* ArgoCD Integration für Deployment-Transparenz
* Git als Single Source of Truth
* End-to-End Self-Service Workflow

### 5️⃣ Dokumentation-as-Code

* TechDocs Integration
* Automatische Generierung mit MkDocs
* Versionskontrollierte Entwicklerdokumentation

### 6️⃣ Authentication & Authorization

* OIDC Login via Keycloak
* Automatische Benutzer- und Gruppensynchronisation
* Grundlegende Permission-Modelle

### 7️⃣ Erweiterbarkeit durch Plugins

* Entwicklung eigener React-Plugins
* Material-UI Theming & UI Customization
* Anpassung an Unternehmensanforderungen

### 8️⃣ Produktionsreife Architektur

* Multi-Stage Docker Builds für Sicherheit
* Deployment in dedizierte Kubernetes Namespaces
* Replizierbare Produktionsumgebung (lokal, VM, Cloud)

---

## Business Value

* Reduzierung der Developer Cognitive Load
* Schnellere Projektinitialisierung
* Standardisierte CI/CD & Deployment-Prozesse
* Transparenz über Service Ownership
* Verbesserte Developer Experience (DX)

---


 **Architektur-Roadmap-Darstellung** deiner *Internal Developer Platform (Platform Engineering Initiative)* :

1. **Zielarchitektur (Production Architecture Overview)**
2. **Technische Integrationsarchitektur**
3. **Implementierungs-Roadmap (Phasenmodell)**

---

# 1️⃣ Zielarchitektur – Internal Developer Platform (Production View)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AUbMV4oMJmpArll4WJfltiQ.png)

![Image](https://wso2.cachefly.net/wso2/sites/all/image_resources/choreo/internal-developer-platform-diagram.webp)

![Image](https://d2908q01vomqb2.cloudfront.net/fe2ef495a1152561572949784c16bf23abb28057/2021/10/14/GitOpsEKS-1.jpg)

![Image](https://www.infracloud.io/assets/img/uploads/2019/12/argocd_architecture.png)

### Architektur-Überblick

**User Layer**

* Entwickler
* Platform Team
* DevOps

⬇

**Developer Portal Layer**

* Backstage

  * Software Catalog
  * Software Templates (Golden Path)
  * TechDocs
  * Kubernetes Plugin
  * ArgoCD Plugin
  * Custom Plugins

⬇

**Integration Layer**

* GitHub (Repos, Org, Discovery)
* GitHub Actions (CI/CD)
* GitHub Container Registry (Images)
* Keycloak (OIDC SSO)
* Argo CD (GitOps)

⬇

**Runtime Layer**

* Kubernetes

  * Namespaces (Prod / Dev / Staging)
  * Workloads
  * Services
  * Ingress

---

# 2️⃣ Technische Integrationsarchitektur (Flow-Diagramm Erklärung)

## End-to-End Self-Service Workflow

1. Entwickler loggt sich via **Keycloak OIDC** ein
2. Erstellt Service über Golden Path Template
3. Backstage erzeugt:

   * GitHub Repository
   * CI/CD Workflow
   * Dockerfile (Multi-Stage)
4. GitHub Actions:

   * Build
   * Push zu GHCR
   * Update GitOps Repo
5. ArgoCD deployt automatisch nach Kubernetes
6. Backstage zeigt:

   * Service Ownership
   * Kubernetes Status
   * Deployment Status
   * Dokumentation

➡ **Git = Single Source of Truth**

---

# 3️⃣ Roadmap – Implementierungsphasen

![Image](https://cdn.thenewstack.io/media/2024/11/344ba615-platform-journey-map-2.png)

![Image](https://backstage.io/assets/images/package-architecture.drawio-15aac8979d89a6c2f7eb24f04d8d3b32.svg)

![Image](https://media2.dev.to/dynamic/image/width%3D1280%2Cheight%3D720%2Cfit%3Dcover%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F4oxdwy8cxkrbi9hnuwm2.png)

![Image](https://opencredo.com/assets/images/66bcbeed055d7275d5bf7c87_AD_4nXcUNpvE41OXGXClhW-MzDPMVnkgMBH8GZGKXgUvMqDEqJmGMFlMuncsyNTS4agn_yua9N96UysrIN64N9JaN4FHimtUNwduuVIAb8iwa5dmhvtnojEtV40STCbD9WXgwdPbainkOFD1wM3cztAmnp5BattO.png)

## 🔹 Phase 1 – Foundation

* Backstage lokal starten
* Docker Setup
* Software Catalog konfigurieren
* GitHub Integration
* Sample Organizations importieren

## 🔹 Phase 2 – Standardisierung

* Golden Path Templates
* GitHub Actions Pipelines
* Multi-Stage Docker Builds
* GHCR Integration
* Namespace-Strategie definieren

## 🔹 Phase 3 – Production Enablement

* Kubernetes Deployment
* ArgoCD GitOps Integration
* Workload Mapping via Annotations
* OIDC mit Keycloak
* Permission Model

## 🔹 Phase 4 – Erweiterbarkeit & Skalierung

* Custom Plugins entwickeln
* UI Theming (Material UI)
* Metriken zur Adoption
* Self-Hosted Production Setup
* CBA Exam Vorbereitung

---

# 4️⃣ Kompakte Architektur-Zusammenfassung (Executive View)

**Die Plattform verbindet:**

Developer Experience + Automation + Governance + GitOps + Kubernetes Visibility

Sie ermöglicht:

* Vollständige Self-Service Software-Erstellung
* Standardisierte Produktionspipelines
* Transparente Ownership-Struktur
* Produktionsreife Container- und Deployment-Strategie
* Zentrale Developer Experience Plattform

---


# **Spezifisch Architektur für ein Kubernetes-Cluster**

---

# 🏗 Internal Developer Platform – Kubernetes-basierte Zielarchitektur

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2AHIshxnsx-mnOPjVqPDnB_w.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AUsoRh3pKIEzO-fmOZrKcZA.png)

![Image](https://miro.medium.com/1%2AcTriV-5n67K_IVBvdn-dHg.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A743/1%2AyWazZNylMUHEbwPt1pyzGw.webp)

---

## 🔷 1️⃣ Architektur Layer

### 👤 User Layer

* Developer
* Platform Engineer

⬇

### 🖥 Developer Portal Layer

* Backstage

  * Software Catalog
  * Golden Path Templates
  * TechDocs
  * Kubernetes Plugin
  * ArgoCD Plugin

Backstage läuft als Deployment **im Kubernetes-Cluster**.

⬇

### 🔐 Identity Layer

* Keycloak

  * OIDC Authentication
  * Group Mapping
  * RBAC Mapping

⬇

### 🔁 CI/CD & GitOps Layer

* GitHub
* GitHub Actions
* GitHub Container Registry
* Argo CD

⬇

### ☸ Runtime Layer

* Kubernetes Cluster

  * Namespaces (dev / staging / prod)
  * Deployments
  * Services
  * Ingress
  * ConfigMaps / Secrets

---

# 🔄 End-to-End Workflow (Dein echtes Setup)

### 1️⃣ Login

Developer loggt sich via Keycloak (OIDC) in Backstage ein.

### 2️⃣ Service Creation

Golden Path Template erzeugt:

* Neues GitHub Repo
* Standardisiertes Dockerfile (Multi-Stage)
* GitHub Actions Workflow
* Kubernetes Manifeste
* GitOps Repository Eintrag

### 3️⃣ Build & Push

GitHub Actions:

* Build Docker Image
* Push zu GHCR
* Update GitOps Repo

### 4️⃣ Deployment

ArgoCD:

* Erkennt Änderung im Git
* Deployt automatisch ins Kubernetes Namespace

### 5️⃣ Visibility

Backstage zeigt:

* Deployment Status
* Pod Health
* Service Ownership
* Dokumentation (TechDocs)

---

# 🔐 Sicherheitsmodell (Dein Projekt-spezifisch)

* OIDC via Keycloak
* RBAC via Kubernetes Roles
* Namespace Isolation
* GitHub Actions mit minimalen Registry Permissions
* Multi-Stage Docker Builds (kein Build-Tool im Final Image)

---

# 📦 Was diese Architektur NICHT enthält

* ❌ Kein Crossplane
* ❌ Kein Terraform
* ❌ Kein Cloud Provisioning Layer
* ❌ Kein Service Mesh

Eine **reine Kubernetes-basierte Internal Developer Platform mit GitOps**.

---


* ✅ Kubernetes Cluster
* ✅ Backstage läuft im Cluster
* ✅ ArgoCD läuft im selben Cluster
* ✅ GitHub Organisation (keine Einzel-Repos)
* ✅ GitHub Actions + GHCR
* ✅ Keycloak OIDC
* ❌ Kein Crossplane
* ❌ Kein Terraform

---

# 🏗 Final Architecture – Internal Developer Platform 

![Image](https://miro.medium.com/1%2Apvo0SXZfqVEl_J-60-g4cg.gif)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2AHIshxnsx-mnOPjVqPDnB_w.png)

![Image](https://raw.githubusercontent.com/StarpTech/k8s-gitops/main/workflow-v11.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AcoMYqPTL2LKeit2tgwndRg.png)

---

# 🔷 1️⃣ High-Level Architecture

## 👤 Users

Developers & Platform Engineers

⬇

## 🖥 Developer Portal (im selben Cluster)

* Backstage (Deployment im Namespace `platform`)
* Argo CD (Namespace `argocd`)

---

## 🔐 Identity Layer

* Keycloak

  * OIDC
  * Gruppen-Mapping
  * RBAC-Zuweisung

Backstage nutzt Keycloak für Login und Gruppen-Synchronisierung.

---

## 🔁 Source of Truth Layer

* GitHub Organisation

  * Service Repositories
  * GitOps Repository
  * Template Repositories

* GitHub Actions

* GitHub Container Registry

GitHub Org = zentrales Ownership- & Governance-Modell.

---

## ☸ Runtime Layer – Kubernetes Cluster

Namespaces z. B.:

* `platform` → Backstage
* `argocd` → ArgoCD
* `dev-*` → Entwicklungsservices
* `prod-*` → Produktionsservices

ArgoCD synchronisiert Git → Cluster.

---

# 🔄 Dein echter End-to-End Flow

### 1️⃣ Login

Developer → Keycloak → Backstage

### 2️⃣ Service Creation (Golden Path)

Backstage Template erstellt:

* Neues Repo in GitHub Org
* CI Workflow
* Dockerfile (Multi-Stage)
* Kubernetes Manifeste
* ArgoCD Application

### 3️⃣ Build Phase

GitHub Actions:

* Docker Build
* Push zu GHCR
* Commit ins GitOps Repo

### 4️⃣ GitOps Deployment

ArgoCD:

* erkennt Commit
* synced ins Ziel-Namespace
* überwacht Drift

### 5️⃣ Visibility

Backstage:

* Kubernetes Plugin zeigt Pods
* ArgoCD Plugin zeigt Sync Status
* Catalog zeigt Ownership

---

# 🔒 Sicherheits- & Governance-Modell

* Namespace Isolation
* OIDC Auth via Keycloak
* GitHub Org Team Mapping
* Least-Privilege GitHub Actions Permissions
* Multi-Stage Docker Builds
* Git = Single Source of Truth

---

# 🧠 Warum diese Architektur sauber ist

* Plattform-Komponenten laufen getrennt von Business-Workloads
* GitOps sorgt für deterministische Deployments
* Kein zusätzlicher Infra-Provisioning Layer → reduziert Komplexität
* Skalierbar durch Namespace-Strategie
* Voll kompatibel mit CBA-Prüfungsinhalten

---

 Jetzt eine dieser 3 professionellen Varianten erstellen:

### 🔹 Option A – C4 Architecture (für Architektur-Review geeignet)

### 🔹 Option B – Management Executive Slide (1 Seite, sehr clean)

### 🔹 Option C – Technisches Deep-Dive Diagramm mit Netzwerk-Ports & RBAC



---

===========================================
# Schritt 1: Überprüfen, ob Backstage läuft
===========================================


```bash
systemctl status backstage
```

<img width="838" height="680" alt="image" src="https://github.com/user-attachments/assets/420bdbc8-ea5f-4e0f-b6df-4bd0c89c5f17" />

# Ergebnis


<img width="1095" height="970" alt="image" src="https://github.com/user-attachments/assets/9004d71a-bdee-4fb0-b9fe-c1c8e2dc74d4" />


# Schritt 2: Template-Struktur untersuchen

Untersuchung der Standard-Templates, um deren Struktur zu verstehen. Suche nach `template.yaml`-Dateien:

```bash
find /root/labs/developer-portal -name "template.yaml" -o -name "*.yaml" | grep -i template
```
<img width="1308" height="328" alt="image" src="https://github.com/user-attachments/assets/6bdebbc8-12fa-42e7-bab9-7154dcd9aa3d" />



# Schritt 3: Template-Komponenten analysieren

Erstellung einer Verzeichnisstruktur zum Studium der Templates:

```bash
mkdir -p /root/labs/templates-study
```

Navigieren Sie in das Studienverzeichnis:

```bash
cd /root/labs/templates-study
```

Laden Sie ein Beispiel-Template herunter, um die Struktur zu verstehen:

```bash
curl -o sample-template.yaml https://raw.githubusercontent.com/backstage/software-templates/main/scaffolder-templates/react-ssr-template/template.yaml
```

<img width="1463" height="306" alt="image" src="https://github.com/user-attachments/assets/5d9efa88-7fb6-4042-b1f0-c896cf95e516" />


Untersuchen Sie die Template-Struktur:

```bash
cat sample-template.yaml
```
<img width="828" height="492" alt="image" src="https://github.com/user-attachments/assets/a33b97b9-6010-42c4-b5d5-b3dd9dfea918" />

Hier die ganze yaml file

```yaml
apiVersion: scaffolder.backstage.io/v1beta3
kind: Template
metadata:
  name: react-ssr-template
  title: React SSR Template
  description: Create a website powered with Next.js
  tags:
    - recommended
    - react
spec:
  owner: web@example.com
  type: website
  parameters:
    - title: Provide some simple information
      required:
        - component_id
        - owner
      properties:
        component_id:
          title: Name
          type: string
          description: Unique name of the component
          ui:field: EntityNamePicker
        description:
          title: Description
          type: string
          description: Help others understand what this website is for.
        owner:
          title: Owner
          type: string
          description: Owner of the component
          ui:field: OwnerPicker
          ui:options:
            allowedKinds:
              - Group
    - title: Choose a location
      required:
        - repoUrl
      properties:
        repoUrl:
          title: Repository Location
          type: string
          ui:field: RepoUrlPicker
          ui:options:
            allowedHosts:
              - github.com
  steps:
    - id: template
      name: Fetch Skeleton + Template
      action: fetch:template
      input:
        url: ./skeleton
        copyWithoutRender:
          - .github/workflows/*
        values:
          component_id: parameters.component_id
          description: "{{ parameters.description }}"
          destination: parameters.repoUrl
          owner: "{{ parameters.owner }}"
root@patrickaboudou-backstage-dev-wrf:~/labs/templates-study# 

### Schritt 4: Template-Komponenten identifizieren

Templates bestehen aus mehreren zentralen Bestandteilen:

* **Metadata**: Name, Beschreibung, Tags
* **Spec.parameters**: Formularfelder für Benutzereingaben
* **Spec.steps**: Aktionen, die während des Scaffoldings ausgeführt werden
* **Spec.output**: Links und Informationen, die nach der Erstellung angezeigt werden

## Was sind Software-Templates in Backstage?

Software-Templates (auch **Scaffolder** genannt) helfen Entwicklerinnen und Entwicklern, neue Projekte schnell zu erstellen und dabei organisatorische Standards einzuhalten. Sie lösen mehrere Herausforderungen:

- **Konsistenz**: Jeder neue Service folgt denselben Mustern und enthält die erforderlichen Dateien  
- **Geschwindigkeit**: Entwickler beginnen nicht bei null, sondern erhalten eine funktionierende Grundlage  
- **Einhaltung von Standards**: Templates binden Best Practices, Sicherheitsanforderungen und Tooling ein  
- **Reduzierte kognitive Last**: Entwickler konzentrieren sich auf die Business-Logik statt auf Boilerplate-Setup  

Man kann sich Templates als „Baupläne“ oder „Cookiecutter“-Werkzeuge vorstellen, die mit nur wenigen Formulareingaben vollständige, sofort einsatzbereite Projekte generieren.

==========================================
---



```bash
cd /root/labs/developer-portal
```
<img width="1591" height="503" alt="image" src="https://github.com/user-attachments/assets/af28e554-6025-4d65-ac56-9f5cbf72b8f4" />


## Erstellen Sie ein Templates-Verzeichnis:

```bash
mkdir -p templates/nodejs-service-template
```

Navigieren Sie in Ihr Template-Verzeichnis:

```bash
cd templates/nodejs-service-template
```

<img width="912" height="753" alt="image" src="https://github.com/user-attachments/assets/47107061-fa25-4feb-8077-f6e2b6f80a29" />


Erstellen Sie Verzeichnisse für die Template-Komponenten:

```bash
mkdir -p skeleton docs
```


### Erklärung der Verzeichnisstruktur:

* `templates/`: Hier befinden sich alle Templates der Organisation
* `nodejs-service-template/`: Der Ordner für dieses spezifische Template
* `skeleton/`: Template-Dateien, die kopiert und verarbeitet werden
* `docs/`: Dokumentation zur Verwendung dieses Templates

---

## Schritt 2: Template-Metadaten definieren

Erstellen Sie die Template-Definitionsdatei. Erstellen Sie im Code-Editor-Tab eine Datei mit dem Namen `template.yaml` im Verzeichnis `nodejs-service-template`:

```yaml
apiVersion: scaffolder.backstage.io/v1beta3
kind: Template
metadata:
  name: nodejs-service-template
  title: Node.js Microservice Template
  description: Create a new Node.js microservice with Express, testing, and Docker support
  tags:
    - nodejs
    - microservice
    - express
    - recommended
  links:
    - url: https://docs.company.com/templates/nodejs
      title: Node.js Service Standards
      icon: docs
    - url: https://github.com/company/nodejs-template-examples
      title: Example Services
      icon: github
spec:
  owner: platform-team
  type: service
  # Parameters, steps, and output will be added in subsequent tasks
```
Als Datei speichern

`/root/labs/developer-portal/templates/nodejs-service-template/template.yaml`.


```bash
yamllint template.yaml
```

Dann

```bash
Ctrl + O
```

Enter
```bash
Ctrl + X
```

## Prüfen, ob die Datei gespeichert wurde


```bash
ls
```
oder
```bash
cat template.yaml
```

<img width="1011" height="196" alt="image" src="https://github.com/user-attachments/assets/fe4e2cf5-03ce-4178-9ff4-399fa36d8c8f" />


### Erklärung der wichtigsten Metadatenfelder:

* **apiVersion**: Verwendet die Scaffolder-API-Version von Backstage (immer `scaffolder.backstage.io/v1beta3`)
* **kind: Template**: Kennzeichnet dies als Software-Template-Entität
* **metadata.name**: Eindeutiger Bezeichner für dieses Template (wird in URLs und Referenzen verwendet)
* **metadata.title**: Für Menschen lesbarer Name, der im Template-Katalog angezeigt wird
* **metadata.description**: Kurze Beschreibung dessen, was dieses Template erstellt
* **metadata.tags**: Labels für Filterung und Auffindbarkeit im Template-Katalog
* **metadata.links**: Hilfreiche Ressourcen zu diesem Template
* **spec.owner**: Team oder Person, die für die Pflege dieses Templates verantwortlich ist
* **spec.type**: Kategorie dessen, was dieses Template erstellt (Service, Website, Bibliothek usw.)

---

## Schritt 3: Template-Tags und Auffindbarkeit verstehen

Tags helfen Entwicklerinnen und Entwicklern, das richtige Template für ihre Anforderungen zu finden. Wählen Sie Tags, die Folgendes widerspiegeln:

* **Technologie**: nodejs, react, python, java
* **Architektur**: microservice, monolith, serverless, api
* **Zweck**: frontend, backend, library, tool
* **Reifegrad**: recommended, experimental, deprecated

Aktualisieren Sie Ihr Template, um spezifischere Tags einzubinden:

```yaml
metadata:
  name: nodejs-service-template
  title: Node.js Microservice Template
  description: Create a new Node.js microservice with Express, testing, and Docker support
  tags:
    - nodejs
    - microservice
    - express
    - rest-api
    - docker
    - typescript
    - recommended
    - backend
```

Wie das  **Update** in meiner `template.yaml` (ersetzen/erweitern) gemacht wird.


<img width="877" height="1071" alt="image" src="https://github.com/user-attachments/assets/1837bb47-4a31-48f6-83ec-006db2cf2f56" />



### 1) Datei öffnen

```bash
nano template.yaml
```

### 2) In `metadata:` den `tags:` Block so ändern

Ersetze das hier:

```yaml
tags:
  - nodejs
  - microservice
  - express
  - recommended
```

durch das hier:

```yaml
tags:
  - nodejs
  - microservice
  - express
  - rest-api
  - docker
  - typescript
  - recommended
  - backend
```

### 3) Änder/Update -Speichern und prüfen


```yaml
apiVersion: scaffolder.backstage.io/v1beta3
kind: Template
metadata:
  name: nodejs-service-template
  title: Node.js Microservice Template
  description: Create a new Node.js microservice with Express, testing, and Docker support
  tags:
    - nodejs
    - microservice
    - express
    - rest-api
    - docker
    - typescript
    - recommended
    - backend
  links:
    - url: https://docs.company.com/templates/nodejs
      title: Node.js Service Standards
      icon: docs
    - url: https://github.com/company/nodejs-template-examples
      title: Example Services
      icon: github
spec:
  owner: platform-team
  type: service
  # Parameters, steps, and output will be added in subsequent tasks
```

Nano: **CTRL+O**, Enter, **CTRL+X**

Dann prüfen:

```bash
cat template.yaml
```


**Step 4: Template Documentation** 

## Ziel

Du sollst eine Datei erstellen:

`/root/labs/developer-portal/templates/nodejs-service-template/docs/README.md`

mit dem Inhalt, den dein Lehrer gegeben hat.

---

## 1) Prüfen, dass du im richtigen Ordner bist

```bash
pwd
ls
```

Du solltest sowas sehen:

* `docs`
* `skeleton`
* `template.yaml`

```md
# Node.js Microservice Template

This template creates a production-ready Node.js microservice with industry best practices built-in.

## What's Included

- **Express.js** web framework with TypeScript
- **Jest** testing framework with coverage reports
- **Docker** containerization with multi-stage builds
- **ESLint** and **Prettier** for code quality
- **GitHub Actions** CI/CD pipeline
- **Swagger/OpenAPI** documentation
- **Health check** endpoints for monitoring

## When to Use This Template

Use this template when you need to create:
- REST APIs and microservices
- Backend services that integrate with other systems
- Services that need to be containerized and deployed to Kubernetes
- APIs that require formal documentation and testing

## Don't Use This Template For

- Frontend applications (use the React template instead)
- Serverless functions (use the Lambda template)
- Data processing jobs (use the Data Pipeline template)
- Static websites or documentation sites

## After Generation

1. Review the generated `README.md` for service-specific setup
2. Update the OpenAPI specification in `docs/api.yaml`
3. Add your business logic to `src/routes/`
4. Run tests with `npm test` 
5. Start development with `npm run dev`

## Support

- **Template owner:** Platform Team
- **Documentation:** https://docs.company.com/templates/nodejs
- **Issues:** Contact platform-team@company.com
```

---

## 4) Speichern und schließen (Nano)

* Speichern: **CTRL + O**
* Enter drücken
* Schließen: **CTRL + X**

---

## 5) Kontrollieren, dass es wirklich gespeichert wurde

```bash
ls -la docs
cat docs/README.md
```

Wenn `cat` den Text ausgibt, ist alles korrekt.

---

## Alternative (schneller, ohne Editor)

Wenn du lieber **ohne nano** direkt erstellen willst, nutze das hier:

```bash
cat > docs/README.md <<'EOF'
# Node.js Microservice Template

This template creates a production-ready Node.js microservice with industry best practices built-in.

## What's Included

- **Express.js** web framework with TypeScript
- **Jest** testing framework with coverage reports
- **Docker** containerization with multi-stage builds
- **ESLint** and **Prettier** for code quality
- **GitHub Actions** CI/CD pipeline
- **Swagger/OpenAPI** documentation
- **Health check** endpoints for monitoring

## When to Use This Template

Use this template when you need to create:
- REST APIs and microservices
- Backend services that integrate with other systems
- Services that need to be containerized and deployed to Kubernetes
- APIs that require formal documentation and testing

## Don't Use This Template For

- Frontend applications (use the React template instead)
- Serverless functions (use the Lambda template)
- Data processing jobs (use the Lambda template)
- Static websites or documentation sites

## After Generation

1. Review the generated `README.md` for service-specific setup
2. Update the OpenAPI specification in `docs/api.yaml`
3. Add your business logic to `src/routes/`
4. Run tests with `npm test` 
5. Start development with `npm run dev`

## Support

- **Template owner:** Platform Team
- **Documentation:** https://docs.company.com/templates/nodejs
- **Issues:** Contact platform-team@company.com
EOF
```

<img width="887" height="1075" alt="image" src="https://github.com/user-attachments/assets/698b95ca-70b5-42a8-91ef-e6a0ef4f3119" />


Danach prüfen:

```bash
cat docs/README.md
```

---

<img width="909" height="966" alt="image" src="https://github.com/user-attachments/assets/5dfd30ee-b023-4ae7-9d27-825732b34ebc" />


### Tag-Strategie:

* **nodejs, express, typescript**: Technologie-Stack
* **microservice, rest-api, backend**: Architektur und Zweck
* **docker**: Enthaltene Deployment-Methode
* **recommended**: Bevorzugtes und empfohlenes Template

---

## Schritt 4: Template-Dokumentation hinzufügen

Erstellen Sie eine Dokumentation für die Template-Nutzer. Erstellen Sie im Code-Editor-Tab eine README-Datei im `docs`-Verzeichnis:

```md
# Node.js Microservice Template

This template creates a production-ready Node.js microservice with industry best practices built-in.

## What's Included

- **Express.js** web framework with TypeScript
- **Jest** testing framework with coverage reports
- **Docker** containerization with multi-stage builds
- **ESLint** and **Prettier** for code quality
- **GitHub Actions** CI/CD pipeline
- **Swagger/OpenAPI** documentation
- **Health check** endpoints for monitoring

## When to Use This Template

Use this template when you need to create:
- REST APIs and microservices
- Backend services that integrate with other systems
- Services that need to be containerized and deployed to Kubernetes
- APIs that require formal documentation and testing

## Don't Use This Template For

- Frontend applications (use the React template instead)
- Serverless functions (use the Lambda template)
- Data processing jobs (use the Data Pipeline template)
- Static websites or documentation sites

## After Generation

1. Review the generated `README.md` for service-specific setup
2. Update the OpenAPI specification in `docs/api.yaml`
3. Add your business logic to `src/routes/`
4. Run tests with `npm test` 
5. Start development with `npm run dev`

## Support

- **Template owner:** Platform Team
- **Documentation:** https://docs.company.com/templates/nodejs
- **Issues:** Contact platform-team@company.com
```

Speichern Sie diese Datei als
`/root/labs/developer-portal/templates/nodejs-service-template/docs/README.md`.

---
## Ergebnis

<img width="909" height="966" alt="image" src="https://github.com/user-attachments/assets/5dfd30ee-b023-4ae7-9d27-825732b34ebc" />



## Template-Eigentümerschaft und Lebenszyklus verstehen

Die Eigentümerschaft von Templates ist entscheidend für die Wartung:

* **Owner-Team**: Verantwortlich für die Aktualisierung des Templates
* **Versionierung**: Templates sollten sich mit den organisatorischen Standards weiterentwickeln
* **Stilllegung**: Alte Templates benötigen klare Migrationspfade
* **Dokumentation**: Nutzer benötigen klare Hinweise, wann und wie Templates zu verwenden sind

### Template-Lebenszyklus:

* **Erstellung**: Das Plattform-Team erstellt Templates basierend auf den Anforderungen der Organisation
* **Testen**: Das Template wird mit realen Projekten validiert
* **Freigabe**: Das Template wird nach erfolgreicher Nutzung als „recommended“ eingestuft
* **Wartung**: Regelmäßige Updates für Sicherheit, Abhängigkeiten und Standards
* **Weiterentwicklung**: Neue Funktionen basierend auf Nutzerfeedback
* **Ablösung**: Wird schließlich durch bessere Ansätze ersetzt

Im nächsten Schritt erstellen Sie das Benutzereingabeformular (Parameter-Sektion), mit dem Informationen von Entwicklern gesammelt werden, um das generierte Projekt zu individualisieren.

Sie haben erfolgreich Template-Metadaten definiert, die Ihr Template auffindbar machen und seinen Zweck klar kommunizieren. Diese Grundlage stellt sicher, dass Entwickler Ihr Template finden und verstehen, bevor sie es verwenden.

---

# **Erstellen des Benutzer-Eingabeformulars**

**Erstellen des Benutzer-Eingabeformulars**
In dieser Aufgabe wird der Abschnitt „Parameter“ des Software-Templates erstellt, der das Formular definiert, das Entwickler ausfüllen, wenn sie das Template verwenden. Dieses Formular sammelt die Informationen, die benötigt werden, um das generierte Projekt an die spezifischen Bedürfnisse der Entwickler anzupassen.

### Warum benötigen Templates Benutzer-Eingabeformulare?

---

### Verständnis der Parameterstruktur

#### Schritt 1: Erstellen von Feldern für grundlegende Projektinformationen

#### Schritt 2: Hinzufügen von Repository- und Integrations-Einstellungen

#### Schritt 3: Hinzufügen von technischen Konfigurationsoptionen


---

### Erstellen des Benutzer-Eingabeformulars

In dieser Aufgabe erstellst du den Parameterbereich deines Software-Templates. Dieser definiert das Formular, das Entwickler ausfüllen, wenn sie dein Template verwenden. Das Formular sammelt die Informationen, die benötigt werden, um das generierte Projekt an die jeweiligen Anforderungen anzupassen.

---

### Warum benötigen Templates Benutzer-Eingabeformulare?

Benutzer-Eingabeformulare machen Templates flexibel und wiederverwendbar, da sie eine individuelle Anpassung ermöglichen:

* **Projektbenennung:** Jedes Projekt benötigt eindeutige Namen und Kennungen
* **Konfigurationsoptionen:** Unterschiedliche Teams benötigen möglicherweise unterschiedliche aktivierte Funktionen
* **Repository-Einrichtung:** Projekte benötigen unterschiedliche Git-Repositories und Zuständigkeiten
* **Umgebungseinstellungen:** Entwicklungs- und Produktionskonfigurationen können variieren
* **Integrationsentscheidungen:** Teams können unterschiedliche Datenbanken, CI/CD-Werkzeuge oder Cloud-Anbieter verwenden

Das Formular übersetzt die Benutzerauswahl in Variablen, die den generierten Code anpassen, sodass ein einziges Template für viele verschiedene Anwendungsfälle genutzt werden kann.

---

### Verständnis der Parameterstruktur

Backstage-Template-Parameter verwenden JSON Schema zur Definition der Formularfelder. Dies bietet:

* **Typvalidierung:** Stellt sicher, dass Benutzer geeignete Datentypen eingeben
* **Benutzererlebnis:** Umfangreiche Formularsteuerelemente wie Dropdown-Menüs, Kontrollkästchen und Textbereiche
* **Dokumentation:** Integrierte Hilfetexte und Feldbeschreibungen
* **Bedingte Logik:** Ein- oder Ausblenden von Feldern basierend auf anderen Auswahlen

---

### Schritt 1: Erstellen grundlegender Felder für Projektinformationen

Aktualisiere dein Template, um Benutzer-Eingabeparameter hinzuzufügen. Öffne im Reiter „Code Editor“ die Datei `nodejs-service-template/template.yaml` und füge den Parameterbereich nach den Metadaten hinzu.

---

Aktualisiere dein Template, um Benutzer-Eingabeparameter hinzuzufügen. Öffne im Reiter „Code Editor“ die Datei `nodejs-service-template/template.yaml` und füge den Parameterbereich nach den Metadaten hinzu:

```
apiVersion: scaffolder.backstage.io/v1beta3
kind: Template
metadata:
  name: nodejs-service-template
  title: Node.js Microservice Template
  description: |
    Creates a production-ready Node.js microservice with Express, testing, and Docker support.
    
    ## What this template creates
    
    - **Express.js API** with TypeScript for type safety
    - **Testing setup** with Jest and Supertest
    - **Docker configuration** for containerized deployment  
    - **GitHub Actions** CI/CD pipeline
    - **OpenAPI documentation** with Swagger UI
    - **Health check endpoints** for monitoring
    - **ESLint and Prettier** for code quality
  
  tags:
    - nodejs
    - microservice
    - express
    - rest-api
    - docker
    - typescript
    - recommended
    - backend
    - api
  
  links:
    - url: https://expressjs.com/
      title: Express.js Documentation
      icon: web
    - url: https://github.com/your-org/nodejs-examples
      title: Example Services
      icon: github

spec:
  owner: platform-team
  type: service
  system: developer-tools
  
  # User input form definition
  parameters:
    - title: Project Information
      required:
        - name
        - description
        - owner
      properties:
        name:
          title: Service Name
          type: string
          description: Name of your new microservice (will be used for repository and package names)
          pattern: '^[a-z0-9-]+$'
          minLength: 3
          maxLength: 50
          ui:autofocus: true
          ui:help: 'Use lowercase letters, numbers, and hyphens only. Example: user-auth-service'
          ui:placeholder: 'my-awesome-service'
        
        description:
          title: Service Description
          type: string
          description: Brief description of what this service does
          minLength: 10
          maxLength: 200
          ui:widget: textarea
          ui:options:
            rows: 3
          ui:help: 'This will appear in README files and service documentation'
          ui:placeholder: 'This service handles user authentication and session management'
        
        owner:
          title: Team Owner
          type: string
          description: Which team will own and maintain this service
          enum:
            - platform-team
            - frontend-team
            - backend-team
            - data-team
            - devops-team
          enumNames:
            - Platform Team
            - Frontend Team  
            - Backend Team
            - Data Team
            - DevOps Team
          ui:help: 'This determines who gets notified about service issues and changes'
```

<img width="1066" height="498" alt="image" src="https://github.com/user-attachments/assets/09ad34dd-ac18-420a-b324-8674379d0b56" />


<img width="1072" height="898" alt="image" src="https://github.com/user-attachments/assets/92f2749a-a61c-4ce2-a970-e8f78fe39988" />


<img width="970" height="1028" alt="image" src="https://github.com/user-attachments/assets/4632d54c-c230-466a-88ab-d08089bc8d4b" />


---

### Erklärung der Formularfeldtypen:

**string mit pattern:** Texteingabe mit Validierung mittels regulärem Ausdruck (der Servicename muss URL-sicher sein)

**string mit minLength/maxLength:** Texteingabe mit Längenbeschränkungen

**Textarea-Widget:** Mehrzeilige Texteingabe für längere Beschreibungen

**Enum-Dropdown:** Vordefinierte Auswahlmöglichkeiten aus einer Liste (Teamzuordnung, Datenbanktyp usw.)

**Boolean-Kontrollkästchen:** Ja/Nein-Umschalter für Funktionsoptionen (CI/CD aktivieren, Swagger einbinden usw.)

**minLength/maxLength:** Stellt angemessene Eingabelängen sicher

**Integer-Eingabe:** Numerische Werte mit Minimal- und Maximalgrenzen (z. B. Portnummern)

**Standardwerte:** Felder werden mit sinnvollen Standardwerten vorausgefüllt

**Template-Ausdrücke:** `{{ parameters.fieldName }}` zur Referenzierung anderer Formularwerte

**Pflichtfelder:** Diese Felder müssen ausgefüllt sein, bevor das Template verwendet werden kann

**ui:help:** Hilfreicher Anleitungstext für Benutzer

**ui:placeholder:** Beispieltext, der die erwartete Eingabe zeigt

**ui:autofocus:** Setzt den Cursor beim Laden des Formulars automatisch auf dieses Feld

**ui:widget:** Anpassung der Darstellung eines Feldes (z. B. Textarea für Zeichenketten)

---
 **Step 2** hinzufügen: eine **zweite Parameter-Sektion** („Repository and Integration“) in `spec.parameters`, ohne Einrückungsfehler.

## Schritt 1: Datei öffnen

```bash
cd /root/labs/developer-portal/templates/nodejs-service-template
nano template.yaml
```

## Schritt 2: `parameters:` komplett ersetzen (Step 1 + Step 2 zusammen)

Suche in `spec:` den Block `parameters:` und ersetze ihn **komplett** durch diesen korrekten Block:

```yaml
  parameters:
    - title: Project Information
      required:
        - name
        - description
        - owner
      properties:
        name:
          title: Service Name
          type: string
          description: Name of your new microservice (will be used for repository and package names)
          pattern: '^[a-z0-9-]+$'
          minLength: 3
          maxLength: 50
          ui:autofocus: true
          ui:help: 'Use lowercase letters, numbers, and hyphens only. Example: user-auth-service'
          ui:placeholder: 'my-awesome-service'

        description:
          title: Service Description
          type: string
          description: Brief description of what this service does
          minLength: 10
          maxLength: 200
          ui:widget: textarea
          ui:options:
            rows: 3
          ui:help: 'This will appear in README files and service documentation'
          ui:placeholder: 'This service handles user authentication and session management'

        owner:
          title: Team Owner
          type: string
          description: Which team will own and maintain this service
          enum:
            - platform-team
            - frontend-team
            - backend-team
            - data-team
            - devops-team
          enumNames:
            - Platform Team
            - Frontend Team
            - Backend Team
            - Data Team
            - DevOps Team
          ui:help: 'This determines who gets notified about service issues and changes'

    - title: Repository and Integration
      required:
        - github_owner
        - repository_name
      properties:
        github_owner:
          title: GitHub Owner
          type: string
          description: Your GitHub username or organization name where the repository will be created
          pattern: '^[a-z0-9-]+$'
          minLength: 1
          maxLength: 39
          ui:help: 'Example: my-github-username or my-company-org. The repository will be created at github.com/[owner]/[repository-name]'
          ui:placeholder: 'your-github-username'

        repository_name:
          title: Repository Name
          type: string
          description: GitHub repository name (usually same as service name)
          pattern: '^[a-z0-9-]+$'
          ui:help: 'Combined with GitHub Owner above to create: github.com/[owner]/[repository-name]'
          ui:placeholder: 'my-awesome-service'

        enable_cicd:
          title: Enable CI/CD Pipeline
          type: boolean
          description: Include GitHub Actions workflow for automated testing and deployment
          default: true
          ui:help: 'Recommended for all services. Creates automated testing on every commit.'

        database_type:
          title: Database Integration
          type: string
          description: Which database will this service use
          enum:
            - none
            - postgresql
            - mysql
            - mongodb
          enumNames:
            - No Database
            - PostgreSQL
            - MySQL
            - MongoDB
          default: postgresql
          ui:help: 'PostgreSQL is recommended for most applications. Choose "none" for stateless services.'
```

**Wichtig zur Einrückung:**

* `parameters:` hat **2 Leerzeichen** voran (weil es unter `spec:` steht).
* Jede Sektion beginnt mit `- title: ...` (auch 4 Leerzeichen vor `-`).

## Schritt 3: Speichern

Nano:

* **CTRL + O**, Enter
* **CTRL + X**

<img width="1110" height="1067" alt="image" src="https://github.com/user-attachments/assets/d9b3cff9-34ed-42ce-8aeb-5641b1b92d3b" />


<img width="1116" height="1057" alt="image" src="https://github.com/user-attachments/assets/bb8b8830-90e9-4019-bbdd-08404097e3cf" />

<img width="1143" height="1029" alt="image" src="https://github.com/user-attachments/assets/2c3e37c1-0ec8-4b24-a6a9-7f995c20bb98" />

<img width="1127" height="1020" alt="image" src="https://github.com/user-attachments/assets/48042cde-e4d0-46b3-afdb-f55528b40885" />


## Schritt 4: YAML prüfen (muss OK sein)

```bash
python3 - <<'PY'
import yaml
yaml.safe_load(open("template.yaml","r",encoding="utf-8"))
print("OK: template.yaml ist gültig")
PY
```



## Ergebniss

<img width="1219" height="949" alt="image" src="https://github.com/user-attachments/assets/d330c691-2134-49a7-a447-e59c8fa1e72e" />



<img width="1067" height="854" alt="image" src="https://github.com/user-attachments/assets/d510a683-f73e-4379-bb4b-e6925d52f7fb" />




<img width="1234" height="970" alt="image" src="https://github.com/user-attachments/assets/0905dbe4-6a92-42b5-8145-e3da57120175" />




<img width="1337" height="998" alt="image" src="https://github.com/user-attachments/assets/5fc35bae-714c-4504-9908-acd1061b309c" />




---

**Datei aussehen**

---


```yaml
# host: 127.0.0.1
```
###  ändern zu

```yaml
host: 0.0.0.0
```

👉 `0.0.0.0` = akzeptiert Verbindungen von außen
👉 `127.0.0.1` = nur lokal

---



```yaml
origin: http://localhost:3000
```

###  ändern zu

```yaml
origin: http://95.217.214.89:3000
```
---

**Finale korrekte Version**

So sollte es am Ende aussehen:

```yaml
backend:
  baseUrl: http://95.217.214.89:7007
  listen:
    port: 7007
    host: 0.0.0.0

  cors:
    origin: http://95.217.214.89:3000
    methods: [GET, HEAD, PATCH, POST, PUT, DELETE]
    credentials: true
```

---

#  **Danach neu starten**

Im Projektordner:

```bash
CTRL + C   # falls läuft stoppen
yarn dev
```

oder

```bash
yarn start
```

---

#  **im Browser öffnen**

```
http://95.217.214.89:3000
```

---

#  Kurz erklärt warum

| Setting               | Warum                            |
| --------------------- | -------------------------------- |
| host: 0.0.0.0         | Server von außen erreichbar      |
| VM-IP statt localhost | Browser kann verbinden           |
| CORS origin           | Frontend darf Backend ansprechen |

---


---

# **Anleitung: Rundgang durch die Projektstruktur**

Bei laufendem **Backstage** erkunden wir die Projektstruktur, um zu verstehen, wie eine **Backstage**-Anwendung organisiert ist. Dieses Wissen ist für die Anpassung und Erweiterung Ihres Portals unerlässlich.

## **Schritt 1: Root-Projektstruktur erkunden**
Beginnen Sie mit der Untersuchung der Hauptprojektverzeichnisse:

```bash
ls -la /root/labs/developer-portal/
```

<img width="1051" height="867" alt="image" src="https://github.com/user-attachments/assets/f79100ba-324b-45c9-9066-e66a097fadaf" />

Die wichtigsten Komponenten sind:

- **`app-config.yaml`** - Zentrale Konfigurationsdatei
- **`packages/`** - Enthält den Anwendungscode (Frontend und Backend)
- **`catalog-info.yaml`** - Metadaten über diese **Backstage**-Instanz selbst
- **`package.json`** - **Node.js**-Abhängigkeiten und Skripte

Dies folgt dem standardmäßigen **Backstage**-Projektaufbau, was es für andere **Backstage**-Entwickler vertraut macht.

## **Schritt 2: Die Monorepo-Architektur entdecken**
Listen Sie das `packages`-Verzeichnis auf, um die Code-Organisation zu verstehen:

```bash
ls -la /root/labs/developer-portal/packages/
```

<img width="1039" height="803" alt="image" src="https://github.com/user-attachments/assets/d0856b86-05a3-4edc-b9eb-604ff500f902" />



<img width="1039" height="803" alt="image" src="https://github.com/user-attachments/assets/5119d2d9-7e75-4b2c-9e94-09feffb6357c" />


<img width="1058" height="828" alt="image" src="https://github.com/user-attachments/assets/1efde67e-4171-40ad-929c-f61c70a6d621" />




<img width="1005" height="878" alt="image" src="https://github.com/user-attachments/assets/d65939a7-661d-409e-81ea-2fb6ad790c73" />


<img width="981" height="468" alt="image" src="https://github.com/user-attachments/assets/2a084b98-0a7a-47f7-b1af-13bca0126943" />



# Das Verzeichnis `packages` enthält:

- **`app`**: Die React-Frontend-Anwendung, mit der Benutzer interagieren
- **`backend`**: Der **Node.js**-**API**-Dienst, der das Portal betreibt

Diese Monorepo-Struktur ermöglicht es Teams, Frontend und Backend unabhängig voneinander zu entwickeln und dennoch synchron zu halten.

## **Schritt 3: Struktur der Frontend-Anwendung untersuchen**
Erkunden Sie, aus welchen Teilen die Benutzeroberfläche besteht:

```bash
ls -la /root/labs/developer-portal/packages/app/src/
```

<img width="1005" height="878" alt="image" src="https://github.com/user-attachments/assets/e398d683-e87b-4363-986b-f0a16b51dab1" />

Das Frontend umfasst:

- **`App.tsx`**: Haupt-React-Komponente, die das gesamte Portal rendert
- **`components/`**: Benutzerdefinierte **UI**-Komponenten für Ihre spezifischen Anforderungen
- **`App.test.tsx`**: Automatisierte Tests zur Qualitätssicherung

Das Verständnis dieser Struktur hilft Ihnen zu wissen, wo Sie benutzerdefinierte Seiten und Komponenten hinzufügen können.

## **Schritt 4: Aufbau des Backend-Dienstes untersuchen**
Sehen Sie, wie der **API**-Dienst strukturiert ist:

```bash
ls -la /root/labs/developer-portal/packages/backend/src/
```

<img width="981" height="468" alt="image" src="https://github.com/user-attachments/assets/f90399c5-1ad8-4565-bb70-62147de2dcf6" />

Das Backend enthält:

- **`index.ts`**: Einstiegspunkt, der den Server startet und Plugins lädt
- **`plugins/`**: Konfiguration für verschiedene **Backstage**-Plugins
- **`types.ts`**: **TypeScript**-Definitionen für benutzerdefinierte Datenstrukturen

Diese Organisation macht deutlich, wo neue **API**-Endpunkte und Integrationen hinzugefügt werden können.

## **Schritt 5: Kernkonfigurationsdateien prüfen**
Betrachten Sie die Hauptkonfigurationsdatei, um zu verstehen, wie **Backstage** konfiguriert ist:

```bash
cat /root/labs/developer-portal/app-config.yaml
```

Diese Datei steuert alle Aspekte Ihrer **Backstage**-Instanz, einschließlich Datenbank, Authentifizierung und Integrationen.

```yaml
app:
  title: Scaffolded Backstage App
  baseUrl: http://95.217.214.89:3000

organization:
  name: My Company

backend:
  # Wird für die Aktivierung der Authentifizierung verwendet, das Geheimnis wird von allen Backend-Plugins geteilt
  # Siehe https://backstage.io/docs/auth/service-to-service-auth für
  # Informationen zum Format
  # auth:
  #   keys:
  #     - secret: ${BACKEND_SECRET}
  baseUrl: http://95.217.214.89:7007
  listen:
    port: 7007
    # Entfernen Sie den Kommentar der folgenden host-Direktive, um an bestimmten Schnittstellen zu binden
    # host: 127.0.0.1
  csp:
    connect-src: ["'self'", 'http:', 'https:']
    # Die Content-Security-Policy-Direktiven folgen dem Helmet-Format: https://helmetjs.github.io/#reference
    # Standardmäßige Helmet-Content-Security-Policy-Werte können entfernt werden, indem der Schlüssel auf false gesetzt wird
  cors:
    origin: http://95.217.214.89:3000
    methods: [GET, HEAD, PATCH, POST, PUT, DELETE]
    credentials: true
  # Dies ist nur für die lokale Entwicklung gedacht, es wird nicht empfohlen, dies in der Produktion zu verwenden
  # Die Produktionsdatenbankkonfiguration wird in app-config.production.yaml gespeichert
  database:
    client: better-sqlite3
    connection: ':memory:'
  # workingDirectory: /tmp # Verwenden Sie dies, um ein Arbeitsverzeichnis für den Scaffolder zu konfigurieren, standardmäßig wird das temporäre Verzeichnis des Betriebssystems verwendet

integrations:
  github:
    - host: github.com
      # Dies ist ein Personal Access Token (PAT) von GitHub. Sie können herausfinden, wie Sie dieses Token generieren, und weitere Informationen
      # zur Einrichtung der GitHub-Integration hier: https://backstage.io/docs/integrations/github/locations#configuration
      token: ${GITHUB_TOKEN}
    ### Beispiel zum Hinzufügen Ihrer GitHub Enterprise-Instanz über die API:
    # - host: ghe.example.net
    #   apiBaseUrl: https://ghe.example.net/api/v3
    #   token: ${GHE_TOKEN}

proxy:
  ### Beispiel zum Hinzufügen eines Proxy-Endpunkts für das Frontend.
  ### Ein typischer Grund dafür ist die Handhabung von HTTPS und CORS für interne Dienste.
  # endpoints:
  #   '/test':
  #     target: 'https://example.com'
  #     changeOrigin: true

# Referenzdokumentation http://backstage.io/docs/features/techdocs/configuration
# Hinweis: Verwenden Sie nach dem Experimentieren mit der Basiskonfiguration CI/CD, um Dokumente zu generieren,
# und einen externen Cloud-Speicher, wenn Sie TechDocs für den Produktionseinsatz bereitstellen.
# https://backstage.io/docs/features/techdocs/how-to-guides#how-to-migrate-from-techdocs-basic-to-recommended-deployment-approach
techdocs:
  builder: 'local' # Alternativen - 'external'
  generator:
    runIn: 'docker' # Alternativen - 'local'
  publisher:
    type: 'local' # Alternativen - 'googleGcs' oder 'awsS3'. Lesen Sie die Dokumentation für die Verwendung von Alternativen.

auth:
  # siehe https://backstage.io/docs/auth/ , um mehr über Authentifizierungsanbieter zu erfahren
  providers:
    # Siehe https://backstage.io/docs/auth/guest/provider
    guest: {}

scaffolder:
  # siehe https://backstage.io/docs/features/software-templates/configuration für Optionen von Softwarevorlagen

catalog:
  import:
    entityFilename: catalog-info.yaml
    pullRequestBranchName: backstage-integration
  rules:
    - allow: [Component, System, API, Resource, Location]
  locations:
    # Lokale Beispieldaten, Dateipfade sind relativ zum Backend-Prozess, typischerweise `packages/backend`
    - type: file
      target: ../../examples/entities.yaml

    # Lokale Beispielvorlage
    - type: file
      target: ../../examples/template/template.yaml
      rules:
        - allow: [Template]

    # Lokale Beispieldaten für die Organisation
    - type: file
      target: ../../examples/org.yaml
      rules:
        - allow: [User, Group]

    ## Entfernen Sie die Kommentare für diese Zeilen, um weitere Beispieldaten hinzuzufügen
    # - type: url
    #   target: https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/all.yaml

    ## Entfernen Sie die Kommentare für diese Zeilen, um eine Beispielorganisation hinzuzufügen
    # - type: url
    #   target: https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/acme-corp.yaml
    #   rules:
    #     - allow: [User, Group]

kubernetes:
  # siehe https://backstage.io/docs/features/kubernetes/configuration für Kubernetes-Konfigurationsoptionen

# siehe https://backstage.io/docs/permissions/getting-started für mehr Informationen über das Berechtigungsframework
permission:
  # wenn dies auf `false` gesetzt wird, werden Berechtigungen deaktiviert
  enabled: true
```

Untersuchen Sie auch die Katalog-Metadaten für die **Backstage**-App selbst:

```bash
cat /root/labs/developer-portal/catalog-info.yaml
```

Diese Datei beschreibt Ihre **Backstage**-Instanz als eine Entität in ihrem eigenen Katalog.

```yaml
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: developer-portal
  description: Ein Beispiel für eine Backstage-Anwendung.
  # Beispiel für optionale Annotationen
  # annotations:
  #   github.com/project-slug: backstage/backstage
  #   backstage.io/techdocs-ref: dir:.
spec:
  type: website
  owner: john@example.com
  lifecycle: experimental
```

---


<img width="1797" height="866" alt="image" src="https://github.com/user-attachments/assets/9701e99f-b968-4e2b-9739-be6cb281e139" />




<img width="1337" height="998" alt="image" src="https://github.com/user-attachments/assets/c500ed15-0f80-4e4c-8d7d-e69cb84e3057" />





========================================================================

---
# Keycloak Integration
---

## 📘 Über dieses Lab

In diesem Lab implementierst du eine produktionsreife Authentifizierung mit **Keycloak** als OpenID Connect (OIDC) Provider.  
Du konfigurierst Realms und Clients, richtest Benutzerverwaltung ein, integrierst die Authentifizierung in Backstage und testest vollständige Login-Workflows.

---

## 🎯 Lernziele

Nach diesem Lab kannst du:

- Keycloak mit Docker produktionsnah deployen
- Realms, Clients und OIDC-Einstellungen für die Backstage-Integration konfigurieren
- Den OIDC-Authentifizierungsprovider in Backstage einrichten
- Vollständige Authentifizierungs-Workflows und User-Sessions testen
- Sicherheits-Best-Practices für Authentifizierung anwenden
- Benutzergruppen und Rollen-Mappings für Berechtigungen konfigurieren
- Keycloak-Benutzer und -Gruppen mit dem Backstage-Katalog synchronisieren

Dieses Hands-on-Lab etabliert eine **Enterprise-Grade-Authentifizierung** für dein Developer Portal.

---

## 🔗 Wichtige Ressourcen

- Authentication Overview  
- OIDC Provider Setup  
- Keycloak Dokumentation  

---

# 🧩 Was du lernen wirst (6 Aufgaben)

---

## 1️⃣ Keycloak zu Docker Compose hinzufügen

Füge den Keycloak Identity Provider zu deinem bestehenden Docker-Compose-Stack hinzu – gemeinsam mit Backstage.


<img width="975" height="668" alt="image" src="https://github.com/user-attachments/assets/1c1d61b2-209f-449e-90de-1fa3c089ff46" />


<img width="843" height="631" alt="image" src="https://github.com/user-attachments/assets/5dbee3cb-727e-40f0-802d-47a198017c71" />




---

## 2️⃣ Backstage Realm und OIDC-Client konfigurieren

Erstelle einen dedizierten Realm für Backstage und konfiguriere den passenden OIDC-Client in Keycloak.

---

## 3️⃣ Backstage Backend für OIDC konfigurieren

Konfiguriere das Backstage-Backend so, dass Benutzer über Keycloak mittels OIDC authentifiziert werden.

---

## 4️⃣ Backstage Frontend für OIDC konfigurieren

Richte das Backstage-Frontend so ein, dass die Keycloak-Anmeldeoption über OIDC angezeigt wird.

---

## 5️⃣ Authentifizierung testen und Benutzer erstellen

Teste den vollständigen Authentifizierungs-Workflow und erstelle Benutzer für verschiedene Zugriffsszenarien.

---

## 6️⃣ Keycloak-Benutzer und -Gruppen mit dem Katalog synchronisieren

Importiere Keycloak-Benutzer und -Gruppen als Entitäten in den Backstage-Katalog.

---


````md
# Keycloak Integration – Docker Setup erweitern

## Schritt 1: Aktuelles Docker-Setup überprüfen

Öffne den **Terminal**-Tab und prüfe, ob Backstage und PostgreSQL laufen:

```bash
cd /root/labs/developer-portal
docker compose ps
````

Du solltest folgende Container sehen:

* `backstage-app`
* `postgres-backstage`

<img width="1342" height="406" alt="image" src="https://github.com/user-attachments/assets/972d7c83-f436-43e6-a45d-fdeaddbcb12e" />

<img width="1337" height="379" alt="image" src="https://github.com/user-attachments/assets/bd77fe9e-f5c6-4db6-9371-0af235cf8d7a" />






Beide sollten den Status **running** (bzw. `healthy` für Postgres) anzeigen.

---

## Schritt 2: Docker Secrets überprüfen

Im Lab sind bereits vorkonfigurierte Docker-Secrets im Verzeichnis `secrets/` vorhanden.

Prüfe den Inhalt:

```bash
ls -la secrets/
```

Du solltest folgende Dateien sehen:

* `postgres_password.txt` – PostgreSQL-Datenbankpasswort (wird über Docker Secrets verwendet)
* `keycloak_admin_password.txt` – Keycloak-Administratorpasswort (wird per Bind-Mount eingebunden)

<img width="1340" height="318" alt="image" src="https://github.com/user-attachments/assets/c4782829-4e34-4af9-95c8-0dc9b0dcf115" />




### 🔐 Sicherheitskonzept

Diese Dateien enthalten Zugangsdaten, die sicher in die Container gemountet werden:

* **PostgreSQL** nutzt native Docker-Secret-Unterstützung (`/run/secrets/...`)
* **Keycloak** verwendet einen Bind-Mount + Custom-Entrypoint, um das Passwort beim Start einzulesen
* Keine Passwörter im Klartext in der `docker-compose.yml`

Das ist deutlich sicherer als das Hinterlegen von Passwörtern als Umgebungsvariablen.

---

## Schritt 3: Keycloak zu Docker Compose hinzufügen

Öffne im **Code Editor**:

```
/root/labs/developer-portal/docker-compose.yml
```

Ersetze den gesamten Inhalt mit folgender Konfiguration:

```yaml
services:
  postgres:
    image: postgres:15
    container_name: postgres-backstage
    restart: unless-stopped
    environment:
      POSTGRES_USER: backstage
      POSTGRES_PASSWORD_FILE: /run/secrets/postgres_password
      POSTGRES_DB: backstage
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U backstage"]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 30s
    networks:
      - backstage-network
    secrets:
      - postgres_password

  keycloak:
    image: quay.io/keycloak/keycloak:24.0
    container_name: keycloak-backstage
    entrypoint: /bin/bash
    command:
      - -c
      - |
        export KEYCLOAK_ADMIN_PASSWORD=$$(cat /secrets/keycloak_admin_password | tr -d '[:space:]')
        /opt/keycloak/bin/kc.sh start-dev
    restart: unless-stopped
    environment:
      KEYCLOAK_ADMIN: admin
      KC_PROXY_HEADERS: xforwarded
      KC_HTTP_ENABLED: "true"
      KC_HOSTNAME_STRICT: "false"
    ports:
      - "8080:8080"
    volumes:
      - keycloak_data:/opt/keycloak/data
      - ./secrets/keycloak_admin_password.txt:/secrets/keycloak_admin_password:ro
    healthcheck:
      test: ["CMD-SHELL", "(echo > /dev/tcp/localhost/8080) 2>/dev/null && exit 0 || exit 1"]
      interval: 10s
      timeout: 5s
      retries: 10
      start_period: 60s
    networks:
      - backstage-network

  backstage:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: backstage-app
    restart: unless-stopped
    ports:
      - "7007:7007"
    environment:
      POSTGRES_HOST: postgres
      POSTGRES_PORT: 5432
      POSTGRES_USER: backstage
      POSTGRES_PASSWORD_FILE: /run/secrets/postgres_password
      POSTGRES_DB: backstage
      NODE_ENV: production
      LOG_LEVEL: info
    depends_on:
      postgres:
        condition: service_healthy
    volumes:
      - ./app-config.yaml:/app/app-config.yaml:ro
      - ./examples:/app/examples:ro
    networks:
      - backstage-network
    secrets:
      - postgres_password

secrets:
  postgres_password:
    file: ./secrets/postgres_password.txt

volumes:
  postgres_data:
    driver: local
  keycloak_data:
    driver: local

networks:
  backstage-network:
    driver: bridge
```




<img width="1080" height="919" alt="image" src="https://github.com/user-attachments/assets/77d5f2d3-cb52-4a6a-8e5b-e55fa79452b3" />


<img width="1143" height="494" alt="image" src="https://github.com/user-attachments/assets/1fa2c1d3-74d9-4d1d-b6b5-06d77dbc94e6" />



<img width="1161" height="230" alt="image" src="https://github.com/user-attachments/assets/b999ff30-5e9e-4229-bdc7-5a9c232758f6" />



---

## 🔐 Wichtige Sicherheitsfeatures

### Docker Secrets

* Zugangsdaten werden als Dateien unter `/run/secrets/` gemountet
* Keine sensiblen Umgebungsvariablen
* Keine Klartext-Passwörter im Compose-File

### PostgreSQL

* Unterstützt `POSTGRES_PASSWORD_FILE` nativ
* Passwort wird direkt aus Secret-Datei gelesen

### Keycloak

* Custom-Entrypoint liest Admin-Passwort vor dem Start
* `start-dev` Modus für Lernumgebung
* `KC_PROXY_HEADERS=xforwarded` für Reverse-Proxy-Unterstützung
* HTTP aktiviert für Lab-HTTPS-Termination
* Healthcheck mit Grace-Period

### Netzwerk

* Gemeinsames `backstage-network`
* Interne Container-Kommunikation isoliert

---

## Schritt 4: Keycloak starten

Starte Keycloak:

```bash
docker compose up -d keycloak
```
<img width="1161" height="230" alt="image" src="https://github.com/user-attachments/assets/9992484d-b0d5-4fc0-ac1b-1ae839aa7baa" />

Logs beobachten:

```bash
docker compose logs -f keycloak
```
<img width="1539" height="962" alt="image" src="https://github.com/user-attachments/assets/84f04ac7-5817-489d-b7d8-ad1963297a2c" />

Warte auf folgende Meldung:

```
Keycloak 24.0.x on JVM (powered by Quarkus) started in XX.XXXs. 
Listening on: http://0.0.0.0:8080
```

<img width="2330" height="925" alt="image" src="https://github.com/user-attachments/assets/73af61e7-5cd6-42c1-abf2-7d028455b21c" />


Danach mit `Ctrl + C` die Logs beenden.

---

## Schritt 5: Alle Services überprüfen

Status prüfen:

```bash
docker compose ps
```

Erwartete Ausgabe:

* `postgres-backstage` → **healthy**
* `keycloak-backstage` → **healthy** (kann ~60 Sekunden dauern)
* `backstage-app` → **running**
<img width="1823" height="143" alt="image" src="https://github.com/user-attachments/assets/5117b34b-de67-4ce8-8e39-9f8937a596a4" />


Keycloak testen:

```bash
curl -s "http://localhost:8080/realms/master" | jq -r '.realm'
```

Erwartete Ausgabe:

```
master
```
<img width="1818" height="203" alt="image" src="https://github.com/user-attachments/assets/9985177d-bbbd-44e3-ae70-4bda816a62bf" />

---

## Schritt 6: Keycloak Admin Console öffnen

Öffne den **Keycloak Admin**-Tab.

⚠ Falls nur ein leerer Bildschirm erscheint:
→ Browser-Tab aktualisieren.

### Login-Daten

**Username:**  

```
admin
```

**Password anzeigen mit:**

```bash
cat secrets/keycloak_admin_password.txt 
```
==> keycloak-admin-1234

<img width="1151" height="179" alt="image" src="https://github.com/user-attachments/assets/b4400fa2-97d8-4eff-9913-1bcf322fa998" />

---

✅ Du hast Keycloak erfolgreich mit sicherem Credential-Management in deinen Docker-Compose-Stack integriert.

Im nächsten Schritt konfigurierst du einen **Backstage-Realm** und einen **OIDC-Client**.

```
```



```

CODE COMPLET
```






```bash

SSH connection established.
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.8.0-90-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Sun Mar  1 03:16:37 PM UTC 2026

  System load:  0.44               Processes:             194
  Usage of /:   12.3% of 74.79GB   Users logged in:       0
  Memory usage: 30%                IPv4 address for eth0: 95.217.210.206
  Swap usage:   0%                 IPv6 address for eth0: 2a01:4f9:c010:ebeb::1


Expanded Security Maintenance for Applications is not enabled.

42 updates can be applied immediately.
22 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


*** System restart required ***
Note: Your bash history is configured to save automatically after each command for easy task verification.
Note: Your bash history is configured to save automatically after each command for easy task verification.
root@patrickaboudou-backstage-keycloak-fmv:~# ^[[200~cd /root/labs/developer-portal~
cd: command not found
root@patrickaboudou-backstage-keycloak-fmv:~# cd /root/labs/developer-portal
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# docker compose ps
NAME                 IMAGE                        COMMAND                  SERVICE     CREATED         STATUS                   PORTS
backstage-app        developer-portal-backstage   "/usr/local/bin/cust…"   backstage   7 minutes ago   Up 7 minutes             0.0.0.0:7007->7007/tcp, [::]:7007->7007/tcp
postgres-backstage   postgres:15                  "docker-entrypoint.s…"   postgres    7 minutes ago   Up 7 minutes (healthy)   5432/tcp
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# ls -la secrets/
total 16
drwx------ 2 root root 4096 Mar  1 15:12 .
drwx------ 9 root root 4096 Mar  1 15:13 ..
-rw-r--r-- 1 root root   20 Mar  1 15:12 keycloak_admin_password.txt
-rw------- 1 root root   31 Mar  1 15:12 postgres_password.txt
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# ^C
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# 
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# cd /root/labs/developer-portal
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# cp docker-compose.yml docker-compose.yml.bak
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# cat > docker-compose.yml <<'EOF'
services:
  postgres:
    image: postgres:15
    container_name: postgres-backstage
    restart: unless-stopped
    environment:
      POSTGRES_USER: backstage
      POSTGRES_PASSWORD_FILE: /run/secrets/postgres_password
      POSTGRES_DB: backstage
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U backstage"]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 30s
    networks:
      - backstage-network
    secrets:
      - postgres_password

  keycloak:
    image: quay.io/keycloak/keycloak:24.0
    container_name: keycloak-backstage
    entrypoint: /bin/bash
    command:
      - -c
      - |
        export KEYCLOAK_ADMIN_PASSWORD=$$(cat /secrets/keycloak_admin_password | tr -d '[:space:]')
        /opt/keycloak/bin/kc.sh start-dev
    restart: unless-stopped
    environment:
      KEYCLOAK_ADMIN: admin
      KC_PROXY_HEADERS: xforwarded
      KC_HTTP_ENABLED: "true"
      KC_HOSTNAME_STRICT: "false"
    ports:
      - "8080:8080"
    volumes:
      - keycloak_data:/opt/keycloak/data
      - ./secrets/keycloak_admin_password.txt:/secrets/keycloak_admin_password:ro
    healthcheck:
      test: ["CMD-SHELL", "(echo > /dev/tcp/localhost/8080) 2>/dev/null && exit 0 || exit 1"]
      interval: 10s
      timeout: 5s
      retries: 10
EOF driver: bridgek:postgres_password.txt.yaml:roes_password
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# docker compose config >/dev/null && echo "OK: docker-compose.yml ist gültig"
OK: docker-compose.yml ist gültig
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# docker compose up -d keycloak
[+] up 9/9
 ✔ Image quay.io/keycloak/keycloak:24.0  Pulled                                                                     5.2s
 ✔ Volume developer-portal_keycloak_data Created                                                                    0.0s
 ✔ Container keycloak-backstage          Started                                                                    0.5s
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# docker compose logs -f keycloak
keycloak-backstage  | Updating the configuration and installing your custom providers, if any. Please wait.
keycloak-backstage  | 2026-03-01 15:37:49,512 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index org.apache.tools.ant.Task: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,553 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index org.springframework.core.io.DefaultResourceLoader: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,553 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index org.springframework.core.io.ResourceLoader: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,555 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index org.springframework.core.io.Resource: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,591 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index org.apache.activemq.artemis.core.journal.RecordInfo: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,591 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index org.apache.activemq.artemis.core.journal.Journal: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,594 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index io.mashona.logwriting.ArrayStore: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,598 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index jakarta.jms.XAConnection: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,598 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index jakarta.jms.XASession: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,599 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index jakarta.jms.XAConnectionFactory: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:49,624 WARN  [io.qua.dep.ind.IndexWrapper] (build-6) Failed to index jakarta.jms.Connection: Class does not exist in ClassLoader QuarkusClassLoader:Deployment Class Loader: PROD for keycloak@130a0f66
keycloak-backstage  | 2026-03-01 15:37:53,764 INFO  [io.qua.dep.QuarkusAugmentor] (main) Quarkus augmentation completed in 8201ms
keycloak-backstage  | 2026-03-01 15:37:55,098 INFO  [org.keycloak.quarkus.runtime.hostname.DefaultHostnameProvider] (main) Hostname settings: Base URL: <unset>, Hostname: <request>, Strict HTTPS: false, Path: <request>, Strict BackChannel: false, Admin URL: <unset>, Admin: <request>, Port: -1, Proxied: true
keycloak-backstage  | 2026-03-01 15:37:56,719 WARN  [io.quarkus.agroal.runtime.DataSources] (JPA Startup Thread) Datasource <default> enables XA but transaction recovery is not enabled. Please enable transaction recovery by setting quarkus.transaction-manager.enable-recovery=true, otherwise data may be lost if the application is terminated abruptly
keycloak-backstage  | 2026-03-01 15:37:57,115 WARN  [org.infinispan.CONFIG] (keycloak-cache-init) ISPN000569: Unable to persist Infinispan internal caches as no global state enabled
keycloak-backstage  | 2026-03-01 15:37:57,201 INFO  [org.infinispan.CONTAINER] (keycloak-cache-init) ISPN000556: Starting user marshaller 'org.infinispan.jboss.marshalling.core.JBossUserMarshaller'
keycloak-backstage  | 2026-03-01 15:37:58,752 INFO  [org.keycloak.quarkus.runtime.storage.legacy.liquibase.QuarkusJpaUpdaterProvider] (main) Initializing database schema. Using changelog META-INF/jpa-changelog-master.xml
keycloak-backstage  | 
keycloak-backstage  | UPDATE SUMMARY
keycloak-backstage  | Run:                        124
keycloak-backstage  | Previously run:               0
keycloak-backstage  | Filtered out:                 0
keycloak-backstage  | -------------------------------
keycloak-backstage  | Total change sets:          124
keycloak-backstage  | 
keycloak-backstage  | 2026-03-01 15:38:00,758 INFO  [org.keycloak.connections.infinispan.DefaultInfinispanConnectionProviderFactory] (main) Node name: node_672756, Site name: null
keycloak-backstage  | 2026-03-01 15:38:00,831 INFO  [org.keycloak.broker.provider.AbstractIdentityProviderMapper] (main) Registering class org.keycloak.broker.provider.mappersync.ConfigSyncEventListener
keycloak-backstage  | 2026-03-01 15:38:00,997 INFO  [org.keycloak.services] (main) KC-SERVICES0050: Initializing master realm
keycloak-backstage  | 2026-03-01 15:38:03,020 INFO  [org.keycloak.services] (main) KC-SERVICES0009: Added user 'admin' to realm 'master'
keycloak-backstage  | 2026-03-01 15:38:03,094 INFO  [io.quarkus] (main) Keycloak 24.0.5 on JVM (powered by Quarkus 3.8.4) started in 8.997s. Listening on: http://0.0.0.0:8080
keycloak-backstage  | 2026-03-01 15:38:03,095 INFO  [io.quarkus] (main) Profile dev activated. 
keycloak-backstage  | 2026-03-01 15:38:03,095 INFO  [io.quarkus] (main) Installed features: [agroal, cdi, hibernate-orm, jdbc-h2, keycloak, logging-gelf, narayana-jta, reactive-routes, resteasy-reactive, resteasy-reactive-jackson, smallrye-context-propagation, vertx]
keycloak-backstage  | 2026-03-01 15:38:03,098 WARN  [org.keycloak.quarkus.runtime.KeycloakMain] (main) Running the server in development mode. DO NOT use this configuration in production.
^C
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# docker compose ps
NAME                 IMAGE                            COMMAND                  SERVICE     CREATED          STATUS                    PORTS
backstage-app        developer-portal-backstage       "/usr/local/bin/cust…"   backstage   28 minutes ago   Up 28 minutes             0.0.0.0:7007->7007/tcp, [::]:7007->7007/tcp
keycloak-backstage   quay.io/keycloak/keycloak:24.0   "/bin/bash -c 'expor…"   keycloak    6 minutes ago    Up 6 minutes (healthy)    0.0.0.0:8080->8080/tcp, [::]:8080->8080/tcp, 8443/tcp
postgres-backstage   postgres:15                      "docker-entrypoint.s…"   postgres    28 minutes ago   Up 28 minutes (healthy)   5432/tcp
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# curl -s "http://localhost:8080/realms/master" | jq -r '.realm'
master
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# ^C
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# cat secrets/keycloak_admin_password.txt
keycloak-admin-1234
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# 

```



Das Bild ist eindeutig: **Keycloak blockt den Zugriff über `http://95.217.210.206:8080`**, weil im **Master-Realm** standardmäßig **SSL required = “external”** aktiv ist.
Heißt: **HTTP ist nur für localhost erlaubt**, aber **für externe Hosts verlangt Keycloak HTTPS** → deshalb „HTTPS required“.

Du hast 3 saubere Wege. Nimm **Option A (empfohlen)**, dann hast du sofort Zugriff ohne Config-Hacks.

---

## Option A (empfohlen): SSH Port-Forward → Zugriff über localhost (funktioniert immer)

Auf **deinem Laptop/PC** (nicht im Server-Terminal) ausführen:

```bash
ssh -L 8080:localhost:8080 root@95.217.210.206
```

Dann im Browser auf deinem Laptop:

* **Keycloak Admin:** `http://localhost:8080/admin/`

Login:

* User: `admin`
* Passwort bekommst du auf dem Server mit:

  ```bash
  cat /root/labs/developer-portal/secrets/keycloak_admin_password.txt
  ```

✅ Vorteil: Keine Änderungen an Keycloak nötig, kein HTTPS-Zwang, sofort nutzbar.

---

## Option B: Plattform-Tab “Keycloak Admin” benutzen (falls vorhanden)

Dein Lab erwähnt explizit einen **Keycloak Admin Tab**. Der läuft meist über einen HTTPS-Reverse-Proxy der Plattform.

* Klick **Keycloak Admin**
* Wenn blank: **Refresh**

✅ Vorteil: Kein SSH nötig.
Wenn du aber trotzdem „HTTPS required“ bekommst, dann nutzt die Plattform nicht korrekt den Proxy-Header → dann Option A oder C.

---

## Option C (Lab-only Fix): SSL-Requirement im Master-Realm auf NONE setzen

Wenn du unbedingt über `http://95.217.210.206:8080` zugreifen willst (nur fürs Lab ok), dann stellst du `sslRequired` im Realm um.

### C.1 In den Keycloak-Container rein

```bash
cd /root/labs/developer-portal
docker exec -it keycloak-backstage bash
```

### C.2 Admin-Passwort aus der Secret-Datei lesen (im Container)

```bash
export KC_PW="$(tr -d '[:space:]' < /secrets/keycloak_admin_password)"
echo "$KC_PW" | wc -c
```

### C.3 Mit kcadm anmelden

```bash
/opt/keycloak/bin/kcadm.sh config credentials \
  --server http://localhost:8080 \
  --realm master \
  --user admin \
  --password "$KC_PW"
```

### C.4 SSL Required im Master-Realm deaktivieren

```bash
/opt/keycloak/bin/kcadm.sh update realms/master -s sslRequired=NONE
```

### C.5 Container verlassen

```bash
exit
```

Jetzt sollte im Browser gehen:

* `http://95.217.210.206:8080/admin/`

⚠️ Hinweis: Das ist **unsicher** (für Lab ok), in Produktion macht man das NICHT so.

---

<img width="1135" height="1061" alt="image" src="https://github.com/user-attachments/assets/3a951360-c90e-4eda-9ee7-2247ec1647af" />


```bash
SSH connection established.
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.8.0-90-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Sun Mar  1 04:10:43 PM UTC 2026

  System load:  0.05               Processes:             200
  Usage of /:   13.5% of 74.79GB   Users logged in:       0
  Memory usage: 51%                IPv4 address for eth0: 95.217.210.206
  Swap usage:   0%                 IPv6 address for eth0: 2a01:4f9:c010:ebeb::1


Expanded Security Maintenance for Applications is not enabled.

42 updates can be applied immediately.
22 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


*** System restart required ***
Last login: Sun Mar  1 15:16:37 2026 from 46.62.185.214
Note: Your bash history is configured to save automatically after each command for easy task verification.
Note: Your bash history is configured to save automatically after each command for easy task verification.
root@patrickaboudou-backstage-keycloak-fmv:~# ip -4 addr | grep -E "inet " | grep -v 127.0.0.1
    inet 95.217.210.206/32 metric 100 scope global dynamic eth0
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-af28a2e8b428
root@patrickaboudou-backstage-keycloak-fmv:~# curl -s "http://localhost:8080/realms/master" | jq -r '.realm'
master
root@patrickaboudou-backstage-keycloak-fmv:~# ssh -L 7007:localhost:7007 -L 8080:localhost:8080 root@95.217.210.206
The authenticity of host '95.217.210.206 (95.217.210.206)' can't be established.
ED25519 key fingerprint is SHA256:soN1NVrokXqW0llgbsorMZHmqK9T/NmNbIl6eMfFOQg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? no
Host key verification failed.
root@patrickaboudou-backstage-keycloak-fmv:~# ssh -L 7007:localhost:7007 -L 8080:localhost:8080 root@95.217.210.206
The authenticity of host '95.217.210.206 (95.217.210.206)' can't be established.
ED25519 key fingerprint is SHA256:soN1NVrokXqW0llgbsorMZHmqK9T/NmNbIl6eMfFOQg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? no
Host key verification failed.
root@patrickaboudou-backstage-keycloak-fmv:~# cd /root/labs/developer-portal
cat secrets/keycloak_admin_password.txt
keycloak-admin-1234
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# ^C
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# cd /root/labs/developer-portal
docker exec -it keycloak-backstage bash
bash-5.1$ export KC_PW="$(tr -d '[:space:]' < /secrets/keycloak_admin_password)"
bash-5.1$ /opt/keycloak/bin/kcadm.sh config credentials \
  --server http://localhost:8080 \
  --realm master \
  --user admin \
  --password "$KC_PW"
Logging into http://localhost:8080 as user admin of realm master
bash-5.1$ /opt/keycloak/bin/kcadm.sh update realms/master -s sslRequired=NONE
bash-5.1$ exit
exit
root@patrickaboudou-backstage-keycloak-fmv:~/labs/developer-portal# 
```




<img width="1632" height="860" alt="image" src="https://github.com/user-attachments/assets/b39a8dfe-3679-47ec-b9e6-8ae526c2500e" />




<img width="1702" height="842" alt="image" src="https://github.com/user-attachments/assets/5f5a140b-a8e8-4594-a3b5-dc12d89f9d9e" />



<img width="1589" height="1194" alt="image" src="https://github.com/user-attachments/assets/67151b5b-7d93-41ed-a917-f140951664c0" />


<img width="1710" height="945" alt="image" src="https://github.com/user-attachments/assets/3808ce9c-7d20-4a7d-85f0-f0afa2a37512" />


<img width="1682" height="891" alt="image" src="https://github.com/user-attachments/assets/88b39c41-1644-4da7-b2db-6009090a2b88" />





<img width="1693" height="1078" alt="image" src="https://github.com/user-attachments/assets/f246aa7c-881a-4436-9f11-774c9a584cb0" />





<img width="1705" height="952" alt="image" src="https://github.com/user-attachments/assets/63e2688d-242e-4cf0-9f09-f683250c3984" />


<img width="1576" height="988" alt="image" src="https://github.com/user-attachments/assets/2e5b41db-22e9-41d2-a9df-62f912ca8c23" />


<img width="1576" height="988" alt="image" src="https://github.com/user-attachments/assets/be76c507-e1e5-4220-8938-4428b41403e4" />


<img width="1581" height="1117" alt="image" src="https://github.com/user-attachments/assets/4624d379-0b32-49a6-82e7-ddf9b2ac3d7b" />




## Was du mir kurz sagen sollst

Willst du **Option A (SSH Port-Forward)** oder **Option C (Realm SSL lockern)**?

Wenn du “A” sagst, gebe ich dir den **exakten** SSH-Befehl passend zu deinem Setup (User/IP/Key), damit du direkt einloggen kannst.




Alles klar: Das, was du da hast (**admin / keycloak-admin-1234**) sind **Keycloak Admin Credentials**, **nicht** das **root SSH Passwort**.

Du findest diese Daten genau hier auf der Lab-Maschine:

## 1) Wo ist das Passwort gespeichert?

In einer Datei im Projektordner:

**Pfad:**
`/root/labs/developer-portal/secrets/keycloak_admin_password.txt`

## 2) Wie zeigst du es an (genau der Befehl)?

```bash
cd /root/labs/developer-portal
cat secrets/keycloak_admin_password.txt
```

Wenn da `keycloak-admin-1234` steht, ist das das Keycloak-Admin-Passwort.

---

## 3) Wie benutzt du diese Daten zum Login?

Das geht **nur**, wenn du die Keycloak Admin Console öffnen kannst, z. B.:

* über den **Keycloak Admin Tab** in der Plattform (empfohlen), oder
* über Port-Forward `http://localhost:8080/admin/`, oder
* wenn HTTP extern erlaubt wäre: `http://95.217.210.206:8080/admin/` (bei dir aktuell blockiert wegen HTTPS required).

Login dann:

* **Username:** `admin`
* **Password:** `keycloak-admin-1234`

---

## 4) Wichtig: Das hilft dir NICHT für `ssh root@95.217...`

Für SSH brauchst du **root-Passwort** oder SSH-Key.
Das Keycloak-Passwort ist dafür komplett unabhängig.

---

### Sag mir kurz, was du erreichen willst:

A) **Nur Keycloak Admin UI öffnen** → dann nehmen wir Option C (sslRequired=NONE) oder Plattform-Tab.
B) **SSH Port-Forward von Windows machen** → dann brauchst du root SSH Passwort/Key; das steht an anderer Stelle (Plattform “SSH credentials”).

Wenn du A willst, schreibe “A” — ich gebe dir sofort die Befehle, um HTTPS-Zwang zu deaktivieren (Lab-only) und du kannst direkt mit `admin/keycloak-admin-1234` einloggen.


<img width="1099" height="236" alt="image" src="https://github.com/user-attachments/assets/f6abec78-a864-4a50-933b-59e81fba144a" />



<img width="1710" height="1088" alt="image" src="https://github.com/user-attachments/assets/f06ea1c6-43e8-47f0-a41e-c2a35afff3a3" />



Perfekt ✅ Das ist **genau** das Keycloak-Admin-Passwort.

* **Keycloak Username:** `admin`
* **Keycloak Password:** `keycloak-admin-1234`
* Datei liegt hier: `/root/labs/developer-portal/secrets/keycloak_admin_password.txt`

Jetzt ist der einzige Blocker: Du bekommst im Browser „**HTTPS required**“, wenn du direkt auf `http://95.217.210.206:8080` gehst.

Da du **kein root-SSH Passwort** für Port-Forwarding hast, machen wir die **Lab-Option C**: Keycloak so konfigurieren, dass HTTP von außen geht.

---

# Fix: „HTTPS required“ deaktivieren (nur fürs Lab)

## 1) In den Keycloak Container gehen

```bash
cd /root/labs/developer-portal
docker exec -it keycloak-backstage bash
```

## 2) Admin Passwort aus der Secret-Datei laden (im Container)

```bash
export KC_PW="$(tr -d '[:space:]' < /secrets/keycloak_admin_password)"
```

## 3) Mit kcadm anmelden (gegen localhost im Container)

```bash
/opt/keycloak/bin/kcadm.sh config credentials \
  --server http://localhost:8080 \
  --realm master \
  --user admin \
  --password "$KC_PW"
```

## 4) SSL Requirement im master Realm auf NONE setzen

```bash
/opt/keycloak/bin/kcadm.sh update realms/master -s sslRequired=NONE
```

## 5) Container verlassen

```bash
exit
```

---





# Danach: Admin Console öffnen & einloggen

Öffne im Browser:

* `http://95.217.210.206:8080/admin/`

Login:

* **Username:** `admin`
* **Password:** `keycloak-admin-1234`

Wenn die Seite leer ist: **Refresh**.

---

<img width="1202" height="827" alt="image" src="https://github.com/user-attachments/assets/0aae8e51-524f-4424-a796-35f08c239c4e" />



<img width="1538" height="821" alt="image" src="https://github.com/user-attachments/assets/b50f0d4b-f128-42b6-b058-077bccc5822a" />


<img width="1318" height="1023" alt="image" src="https://github.com/user-attachments/assets/287ddfdf-32bb-4544-b143-899ab5a23cd4" />



<img width="1648" height="1009" alt="image" src="https://github.com/user-attachments/assets/b670c60f-acb5-4580-82cc-476ef860cd4b" />


# Backstage Realm und OIDC-Client konfigurieren


<img width="1712" height="862" alt="image" src="https://github.com/user-attachments/assets/2f0ac81a-eb9c-4303-bdb2-3efc9bcd844b" />


<img width="1813" height="881" alt="image" src="https://github.com/user-attachments/assets/d8cdab60-80b4-4917-aa77-6bba33c5a3fb" />

<img width="1353" height="973" alt="image" src="https://github.com/user-attachments/assets/25def60d-3922-420b-ad75-f2b48328fe42" />


<img width="1373" height="878" alt="image" src="https://github.com/user-attachments/assets/aba1f719-aa43-4d91-9c80-7bee37eb5df6" />


<img width="1279" height="987" alt="image" src="https://github.com/user-attachments/assets/2649bfed-0e87-4370-a494-970d74aa4409" />

<img width="1441" height="938" alt="image" src="https://github.com/user-attachments/assets/6dfde3ca-cf07-47a9-814c-1bd8e2eb46e7" />



=============================================

# Backstage Realm und OIDC-Client konfigurieren

===================================================



Ein **Realm** in Keycloak ist eine isolierte Domäne, die Benutzer, Rollen und Anwendungen unabhängig von anderen Domänen verwaltet.


```md id="kc-backstage-oidc-setup-de"
# Keycloak Realm und OIDC-Client für Backstage konfigurieren
```

## Schritt 1: Keycloak-Realm-Konzepte verstehen

Die Struktur von Keycloak verstehen:

- **Realm**: Isolierte Sicherheitsdomäne mit eigenen Benutzern und Anwendungen  
- **Client**: Eine Anwendung (z. B. Backstage), die Authentifizierungsdienste nutzt  
- **Benutzer**: Personen, die sich authentifizieren, um auf Anwendungen zuzugreifen  
- **Gruppen/Rollen**: Sammlungen von Berechtigungen, die Benutzern zugewiesen werden  


## Schritt 2: Backstage-Realm erstellen

1. Öffnen Sie den **Keycloak Admin**-Tab, um die Keycloak Admin Console aufzurufen.  
2. Melden Sie sich mit folgenden Zugangsdaten an:

   - **Benutzername:** `admin`  
   - **Passwort:**
 
     ```bash
     cat /root/labs/developer-portal/secrets/keycloak_admin_password.txt
     ```

3. Erstellen Sie ein neues Realm für Backstage:

   - Klicken Sie oben links auf das Dropdown **Master**
   - Wählen Sie **Create Realm**
   - Setzen Sie den **Realm name** auf:

     backstage

   - Klicken Sie auf **Create**



<img width="1389" height="826" alt="image" src="https://github.com/user-attachments/assets/8a422407-1b06-4f52-8f88-0c6332ba4afd" />


<img width="1744" height="940" alt="image" src="https://github.com/user-attachments/assets/11623a55-0e82-4731-8fbf-ec42eced25ef" />


<img width="1731" height="1226" alt="image" src="https://github.com/user-attachments/assets/6495e258-83dd-4efc-8bc4-2a71872c2b03" />


<img width="1745" height="776" alt="image" src="https://github.com/user-attachments/assets/fba52f9f-79b9-4caf-bcd8-256c6b6d3b73" />


<img width="1676" height="985" alt="image" src="https://github.com/user-attachments/assets/b2a4ae50-4913-4630-b2b0-8a0a9eb6989a" />


<img width="1724" height="1169" alt="image" src="https://github.com/user-attachments/assets/046d7e29-c5ba-4f50-8883-78c453cd8c57" />


======================================================
======================================================


```html
SSH connection established.
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.8.0-90-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Sun Mar  1 05:07:30 PM UTC 2026

  System load:  0.01               Processes:             198
  Usage of /:   13.5% of 74.79GB   Users logged in:       0
  Memory usage: 52%                IPv4 address for eth0: 95.217.210.206
  Swap usage:   0%                 IPv6 address for eth0: 2a01:4f9:c010:ebeb::1


Expanded Security Maintenance for Applications is not enabled.

42 updates can be applied immediately.
22 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


*** System restart required ***
Last login: Sun Mar  1 17:07:31 2026 from 46.62.185.214
Note: Your bash history is configured to save automatically after each command for easy task verification.
Note: Your bash history is configured to save automatically after each command for easy task verification.
root@patrickaboudou-backstage-keycloak-fmv:~# cat /opt/tekanaid/backstage_url.txt
https://backstage-app-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com
root@patrickaboudou-backstage-keycloak-fmv:~# ^[[200~cat /opt/tekanaid/keycloak_url.txt~
cat: command not found
root@patrickaboudou-backstage-keycloak-fmv:~# cat /opt/tekanaid/keycloak_url.txt
https://keycloak-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com
root@patrickaboudou-backstage-keycloak-fmv:~# 
````


================================
=================================

### General-Tab

## Schritt 4: Backstage OIDC-Client erstellen

1. Navigieren Sie zu **Clients**

2. Klicken Sie auf **Create client**

3. Konfigurieren Sie:

   * **Client type:** `OpenID Connect`
   * **Client ID:** `backstage`

4. **Next**

### Client-Fähigkeiten konfigurieren

* **Client authentication:** Aktivieren (sichere Client-Credentials)
* **Authorization:** Aktivieren (erweiterte Berechtigungsverwaltung)
* **Standard flow:** Aktivieren (Authorization Code Flow – empfohlen)
* **Direct access grants:** Aktivieren (für API-Zugriff)



## Schritt 5: Öffentliche URLs ermitteln

Vor der Konfiguration der Redirect-URIs müssen Sie Ihre öffentlichen URLs ermitteln.

### Backstage-URL anzeigen

Im Terminal ausführen:

```bash
cat /opt/tekanaid/backstage_url.txt
```

Beispielausgabe:

```
https://backstage-app-yourname-backstage-keycloak.staging.tekanaid.com
```

### Keycloak-URL anzeigen

```bash
cat /opt/tekanaid/keycloak_url.txt
```

Beispielausgabe:

```
https://keycloak-yourname-backstage-keycloak.staging.tekanaid.com
```


## Schritt 7: Gruppen-Mapper für Token-Claims konfigurieren

Damit Backstage weiß, welchen Gruppen ein Benutzer angehört (wichtig für Berechtigungen), muss Keycloak die Gruppenmitgliedschaften im Token bereitstellen.

### Mapper konfigurieren

1. Navigieren Sie zu:
   **Clients → backstage → Client scopes**
2. Klicken Sie auf **backstage-dedicated**
3. Öffnen Sie das Dropdown **Add mapper**
4. Wählen Sie **By configuration**
5. Wählen Sie **Group Membership**

<img width="1673" height="1195" alt="er56" src="https://github.com/user-attachments/assets/5cfa17b5-b8b8-4ecf-a214-b21cec16e566" />


<img width="1673" height="1195" alt="image" src="https://github.com/user-attachments/assets/ae19b70c-890e-4f70-8621-a1c6dae49754" />


### Einstellungen

* **Mapper type:** Group Membership (vorausgewählt)
* **Name:** `groups`
* **Token Claim Name:** `groups`
* **Full group path:** OFF
* **Add to ID token:** ON
* **Add to access token:** ON
* **Add to lightweight access token:** OFF
* **Add to userinfo:** ON
* **Add to token introspection:** ON

Klicken Sie auf **Save**
<img width="1656" height="1144" alt="erg1112" src="https://github.com/user-attachments/assets/8bd76b67-87cb-4b48-a231-f0daacce4699" />


<img width="1395" height="1224" alt="erg111" src="https://github.com/user-attachments/assets/1b9662d5-a329-4880-bf3d-935a4254c206" />

---


---

# Step 5: Public URLs herausfinden 

## 5.1 Backstage Public URL anzeigen

Im Terminal:

```bash
cat /opt/tekanaid/backstage_url.txt
```

## 5.2 Keycloak Public URL anzeigen

```bash
cat /opt/tekanaid/keycloak_url.txt
```

---

# Step 6: OIDC Client Redirect URIs in Keycloak konfigurieren

## 6.1 Keycloak Admin Console öffnen

Öffne deine Keycloak-URL aus `/opt/tekanaid/keycloak_url.txt` im Browser und gehe in die Admin Console (meist `/admin`).

Login:

* Username: `admin`
* Password: (deins aus `cat secrets/keycloak_admin_password.txt`)

* **Username:** `admin`
* **Password:** `keycloak-admin-1234`



## 6.2 Client „backstage“ auswählen

In Keycloak:

* **Clients** → wähle den Client **`backstage`**

  * (Falls der Client noch nicht existiert: **Create client** und als **Client type = OpenID Connect**; Name/Client ID = `backstage` – genau wie dein Lab es vorgibt.)

## 6.3 Redirect/URL-Felder setzen (exakt wie Step 6)

Backstage Public URL aus `/opt/tekanaid/backstage_url.txt`.

### Root URL

`https://YOUR_BACKSTAGE_URL`

### Valid redirect URIs  (WICHTIG: beide hinzufügen)

1. `https://YOUR_BACKSTAGE_URL/api/auth/oidc/handler/frame`
2. `https://YOUR_BACKSTAGE_URL/*`

### Valid post logout redirect URIs

`https://YOUR_BACKSTAGE_URL/*`

### Web origins

`https://YOUR_BACKSTAGE_URL`

Dann **Save**.

---

# Step 7: Group Mapper für Token Claims konfigurieren

Ziel: Keycloak soll **Groups** in das Token schreiben, damit Backstage später RBAC/Permissions bauen kann.

## 7.1 Mapper Pfad in Keycloak

* **Clients** → `backstage`
* Tab **Client scopes**
* Klick **backstage-dedicated**
* **Add mapper** (Dropdown) → **By configuration**
* Wähle **Group Membership**

## 7.2 Mapper Einstellungen (exakt so setzen)

* **Mapper type:** Group Membership (ist vorausgewählt)
* **Name:** `groups`
* **Token Claim Name:** `groups`
* **Full group path:** **OFF**
* **Add to ID token:** **ON**
* **Add to access token:** **ON**
* **Add to lightweight access token:** **OFF**
* **Add to userinfo:** **ON**
* **Add to token introspection:** **ON**

Dann **Save**.


<img width="1325" height="1175" alt="image" src="https://github.com/user-attachments/assets/13b694fa-2b73-472c-8a36-bf7af635b3e4" />



---

# Schnelle Verifikation (damit du sicher bist, dass OIDC stimmt)

## A) OIDC Discovery Endpoint prüfen (Keycloak)

Nimm deine Keycloak Public URL aus `/opt/tekanaid/keycloak_url.txt` und deinen Realm (im Lab meist `backstage` – falls du anders heißt, entsprechend anpassen).

Beispiel:

```bash
KEYCLOAK_URL="$(cat /opt/tekanaid/keycloak_url.txt)"
REALM="backstage"
curl -s "$KEYCLOAK_URL/realms/$REALM/.well-known/openid-configuration" | head
```

Wenn du JSON siehst (issuer, authorization_endpoint, token_endpoint), passt es.

## B) Redirect URIs grob checken

Wenn Login später fehlschlägt, ist zu 90%:

* falsche Public URL (localhost statt tekanaid URL)
* Redirect URI fehlt `/api/auth/oidc/handler/frame`
* Web origins nicht gesetzt

---

# Was kommt danach (damit du nicht hängen bleibst)

Der nächste Task ist typischerweise: **Backstage OIDC Provider konfigurieren** (`app-config.yaml`) + **Sign-in Resolver** (Groups aus Token extrahieren).

Wenn du mir sagst:

1. **Wie heißt dein Realm?** (z. B. `backstage`)
2. Ausgabe von:

```bash
cat /opt/tekanaid/backstage_url.txt
cat /opt/tekanaid/keycloak_url.txt
```

(darfst du anonymisieren, aber Domain-Form muss erkennbar sein)

… dann gebe ich dir **die exakte `app-config.yaml` OIDC-Konfiguration** für Backstage inkl. Resolver für `groups`.



Perfekt — das sind genau die **Public URLs**, die du für Step 6 brauchst:

* **Backstage URL:** `https://backstage-app-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com`
* **Keycloak URL:** `https://keycloak-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com`

(Und ja: das `^[[200~...` ist nur Copy/Paste-Müll. Ignorieren oder einmal `reset` ausführen.)

---

# Step 6: Redirect URIs im Keycloak Client setzen (exakt mit deinen URLs)

## 1) Keycloak Admin Console öffnen

Im Browser öffnen:
`https://keycloak-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com/admin/`

Login:

* **Username:** `admin`
* **Password:** `keycloak-admin-1234`

## 2) Client auswählen


<img width="1744" height="940" alt="image" src="https://github.com/user-attachments/assets/b39646b0-1805-4f53-9d7b-1fa6dc2ca41f" />


<img width="1712" height="862" alt="image" src="https://github.com/user-attachments/assets/a3dc53e2-e9df-41b0-a71c-4ca4c2805e33" />


<img width="1395" height="1224" alt="image" src="https://github.com/user-attachments/assets/d07097a1-2e43-4c9f-88d7-9f8ba695c5c9" />


### Root URL

```
https://backstage-app-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com
```

### Valid redirect URIs  (BEIDE hinzufügen!)

```
https://backstage-app-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com/api/auth/oidc/handler/frame
https://backstage-app-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com/*
```

### Valid post logout redirect URIs

```
https://backstage-app-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com/*
```

### Web origins

```
https://backstage-app-patrickaboudou-yahoo-fr-backstage-keycloak.academy.tekanaid.com
```

Dann **Save**.

---

# Step 7: Group Mapper hinzufügen (Token Claim „groups“)

Pfad:
**Clients → backstage → Client scopes → backstage-dedicated → Add mapper → By configuration → Group Membership**

Dann diese Einstellungen:

* **Name:** `groups`
* **Token Claim Name:** `groups`
* **Full group path:** **OFF**
* **Add to ID token:** **ON**
* **Add to access token:** **ON**
* **Add to lightweight access token:** **OFF**
* **Add to userinfo:** **ON**
* **Add to token introspection:** **ON**
  → **Save**

---

<img width="1673" height="1195" alt="image" src="https://github.com/user-attachments/assets/1ac866d6-60fa-4fa8-9418-3f055c8b0c7a" />



<img width="1657" height="997" alt="image" src="https://github.com/user-attachments/assets/027f11a4-d482-40a6-af17-cd7b73137129" />




## Mini-Check
Wenn dein Realm z. B. `backstage` heißt, teste den Discovery Endpoint:

```bash
KEYCLOAK_URL="$(cat /opt/tekanaid/keycloak_url.txt)"
REALM="backstage"
curl -s "$KEYCLOAK_URL/realms/$REALM/.well-known/openid-configuration" | head
```

---




















## Ergebnis

 erfolgreich konfiguriert:

* Ein dediziertes Keycloak-Realm für Backstage
* Einen OIDC-Client für sichere Authentifizierung
* Korrekte Redirect-URIs mit öffentlicher URL
* Einen Group Mapper zur Übergabe von Gruppenmitgliedschaften

Backstage verfügt nun über eine eigene Authentifizierungsdomäne, die sowohl Benutzeridentität als auch Gruppeninformationen im Token bereitstellt.

```
```

















































=======================================================
### **© ALLE RECHTE VORBEHALTEN**

Dieses Projekt wurde von **Koffitse Aboudou** im Rahmen des Masterarbeit an der **Technischen Hochschule Deggendorf (THD)** im Auftrag der **KUKA GmbH**  realisiert.

**Nutzungshinweise:**

* Jegliche Vervielfältigung, Verbreitung oder kommerzielle Nutzung des Inhalts, der Konzepte oder der Implementierungscodes – auch auszugsweise – ist ohne ausdrückliche schriftliche Genehmigung des Urhebers und der beteiligten Institutionen untersagt.
* Die Inhalte dienen ausschließlich Dokumentations- und Prüfungszwecken im akademischen Kontext. 


**Hinweis**: Dieser Abschnitt der Arbeit stellt nur einen Teil des Gesamtprojekts dar. Das vollständige Projekt ist Eigentum des Unternehmens und daher nicht öffentlich zugänglich. Es handelt sich um ein Projekt, bei dem lediglich ein Teil veröffentlicht wird.























