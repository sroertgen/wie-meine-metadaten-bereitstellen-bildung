# Wie meine Metadaten bereit stellen?

Dieses Dokument basiert auf dem im Rahmen des BMBF geförderten Projektes [JOINTLY](http://jointly.info) entstandenen Dokument [Wie meine Metadaten bereit stellen?](https://kurzelinks.de/wie-metadaten-bereitstellen).
Es wurde an vielen Stellen überarbeitet, insbesondere wurden Hinweise zum [Allgemeinen Metadatenprofil für Bildungsressourcen](https://dini-ag-kim.github.io/amb/latest/) aufgenommen.
Es ist als praktischer Leitfaden für Entwickler:innen und andere Interessierte gedacht, die Metadaten für Lernressourcen oder verwandte Objekte bereitstellen wollen. 
Das Verfahren kann grundsätzlich auch auf andere Arten von Objekten angewendet werden.

## TL;DR

Der Leitfaden empfiehlt die Erstellung einer Sitemap, um Crawler zu den relevanten Objekten zu führen.
Die Daten sollen maschinenlesbar in das HTML einer Webseite eingebettet werden.
Diese Einbettung erfolgt durch JSON-LD in einem `script`-Tag (s. auch [Googles Guide zur Einbettung strukturierter Daten](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data).
Außerdem wird die Orientierung an dem [Allgemeinen Metadatenprofil für Bildungsressourcen (AMB)](https://dini-ag-kim.github.io/amb/latest/) empfohlen, wenn es sich um die Beschreibung von Lernressourcen handelt.
Für andere Objekttypen empfiehlt sich, soweit möglich, eine Nachnutzung von Attributen bei schema.org.

**Lizenz**: Dieses Dokument ist veröffentlicht unter CCO. Der Lizenzhinweis findet sich am Ende des Dokuments. Es darf gerne weiter geteilt und verbessert werden. Dafür wurde es erstellt.

## Worum geht es?

Diese Empfehlung strebt eine möglichst einheitliche Vergabe von Metadaten für im Web publizierte Lehr- und Lernmatieralien an. Konkret soll die **Nutzung gemeinsamer Attribute** und – wo möglich – die **Vergabe einheitlicher Werte** unterstützt werden. 

Das **Basis-Vokabular ist [schema.org](https://schema.org)**, das anerkannt und bereits in vielen Webseiten eingebettet ist.
Dank der [LRMI-Initiative](https://www.dublincore.org/specifications/lrmi/) ist die Beschreibung von Bildungsmaterialien bei schema.org gut unterstützt.
Das [Allgemeinen Metadatenprofil für Bildungsressourcen (AMB)](https://dini-ag-kim.github.io/amb/latest/) nutzt diese Attribute nach und beschreibt als Metadatenprofil die Verwendung der Attribute und die Bereitstellung der Daten.
Dieser Leitfaden folgt im Wesentlichen den dort beschriebenen Empfehlungen.

## LRMI – Learning Resource Metadata Initiative

Siehe http://lrmi.net/about/lrmi/

LRMI ist eine Initiative zur Integration von Metadatenattributen und -werten für die Beschreibung von Bildungsmaterialien in schema.org.
Die Attribute bei LRMI sind also eine Untermenge von schema.org und werden von der [LRMI Task Group](https://www.dublincore.org/groups/lrmi-task-group/) innerhalb der Dublin Core Metadata Initiative (DCMI) gepflegt. 

Einige Properties wurden auf Initiative der LRMI Task Group in schema.org ergänzt, unter anderem:

- [learningResourceType](https://schema.org/learningResourceType)
- [teaches](https://schema.org/teaches)
- [assesses](https://schema.org/assesses)
- [educationalLevel](https://schema.org/educationalLevel)
- [educationalRole](https://schema.org/educationalRole)
- [educationalUse](https://schema.org/educationalUse)
- [interactivityType](https://schema.org/interactivityType)
- [timeRequired](https://schema.org/timeRequired)
- [typicalAgeRange](https://schema.org/typicalAgeRange)
- [isBasedOn](https://schema.org/isBasedOn)
- [license](https://schema.org/license)

Außerdem wurden einige Klassen auf Initiative von LRMI in schema.org ergänzt. Relevant in diesem Kontext sind:

- [LearningResource](https://schema.org/LearningResource)
- [EducationalAudience](https://schema.org/EducationalAudience)

## Allgemeines Metadatenprofil für Bildungsressourcen

Das [Allgemeinen Metadatenprofil für Bildungsressourcen (AMB)](https://dini-ag-kim.github.io/amb/latest/) wird von der [OER-Metadatengruppe](https://wiki.dnb.de/display/DINIAGKIM/OER-Metadatengruppe) innerhalb des [Kompetenzzentrums Interoperable Metadaten (KIM)](https://dini.de/standards) gepflegt.
Das Metadatenprofil nutzt die von LRMI in schema.org ergänzten Attribute und beschreibt genau, welche Attribute, welche Bedeutung haben und welche Werte dort eingetragen werden dürfen.
Dies erleichtert den Datenaustausch und fördert die Interoperabilität, da genau definiert ist, welche Metadatenfelder erwartet werden und welche Werte zulässig sind.
Das Profil stellt außerdem Schema-Dateien bereit, die dabei helfen, die Daten zu validieren.

## Wie meine Daten bereit stellen?

Grundsätzlich werden die Daten verfügbar gemacht, indem zwei Arten von Informationen vorliegen:

- **Sitemap**, um zu erfahren, wo die Informationen liegen
- **JSON-LD**, um die Informationen abzurufen

### Sitemap

Eine Sitemap enthält listenartige Informationen über die auf einer Webseite vorhandenen Seiten.
Das Anlegen einer [Sitemap](https://developers.google.com/search/docs/advanced/sitemaps/overview) führt Suchmaschinen und Crawler direkt zu den relevanten Webseiten, auf denen die eigentlichen Daten finden sind.
Die Sitemap kann dabei spezifisch für einen bestimmten Objekttyp erstellt werden, indem dort beispielsweise nur die Links zur Lernmaterialien bereitgestellt werden.

### [JSON-LD](https://www.w3.org/TR/json-ld/)

Bei der Bereitstellung der Daten folgt das Profil etablierten Best-Practices, die auch hier durch Google beschrieben werden: [Googles Guide zur Einbettung strukturierter Daten](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data).
Die dort zugrunde liegende Technologie ist das Resource Description Framework (RDF).
Dieses Framework ist speziell für den Datenaustausch im Web entwickelt worden und findet besonders im Rahmen der Search Engine Optimization großflächige Anwendung.

Die Darstellung der Daten erfolgt durch [JSON-LD](https://www.w3.org/TR/json-ld/), einer möglichen Serialisierungsform von RDF Daten.
Die Daten werden im HTML der jeweiligen Webseite in einem `script`-Tag dargestellt.
Damit entfällt die Einrichtung einer zusätzlichen Schnittstelle, da das Web und die Daten selbst als Schnittstelle fungieren.

Die maschinenlesbare Beschreibung eines Kurses gemäß dem AMB kann beispielsweise so aussehen:

```html
<script type="application/ld+json">{
{
  "@context": [
    "https://w3id.org/kim/amb/context.jsonld",
    {
      "@language": "de"
    }
  ],
  "id": "https://oer.gitlab.io/OS",
  "type": ["LearningResource", "Course"],
  "name": "Computer Structures and Operating Systems",
  "creator": [
    {
      "id": "https://orcid.org/0000-0002-3064-147X",
      "type": "Person",
      "name": "Jens Lechtenbörger",
      "honorificPrefix": "Dr."
    }
  ],
  "description": "A course on Operating Systems (following the book Operating Systems and Middleware: Supporting Controlled Interaction by Max Hailperin) as part of the module Computer Structures and Operating Systems for 4th-term students in the Bachelor program in Information Systems at the University of Münster, Germany.",
  "about": [
    {
      "id": "https://w3id.org/kim/hochschulfaechersystematik/n079",
      "prefLabel": {
        "de": "Informatik"
      },
      "type": "Concept"
    }
  ],
  "keywords": ["Computer Science", "Operation Systems", "Computer Structures"],
  "isAccessibleForFree": true,
  "conditionsOfAccess": {
    "id": "http://w3id.org/kim/conditionsOfAccess/no_login",
    "type": "Concept"
  },
  "license": {
    "id": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "inLanguage": ["en"],
  "audience": [
    {
      "id": "http://purl.org/dcx/lrmi-vocabs/educationalAudienceRole/student",
      "prefLabel": {
        "en": "student"
      },
      "type": "Concept"
    }
  ],
  "educationalLevel": [
    {
      "id": "https://w3id.org/kim/educationalLevel/level_06",
      "prefLabel": {
        "de": "Bachelor oder äquivalent",
        "en": "Bachelor or equivalent"
      }
    }
  ],
  "hasPart": [
    {
      "id": "https://oer.gitlab.io/OS/Operating-Systems-JiTT.html",
      "type": ["LearningResource", "PresentationDigitalDocument"],
      "name": "JiTT for OS"
    },
    {
      "id": "https://oer.gitlab.io/OS/Operating-Systems-Overview.html",
      "type": ["LearningResource", "PresentationDigitalDocument"],
      "name": "OS Overview"
    },
    {
      "id": "https://oer.gitlab.io/OS/Operating-Systems-Introduction.html",
      "type": ["LearningResource", "PresentationDigitalDocument"],
      "name": "OS Introduction"
    },
    {
      "id": "https://oer.gitlab.io/OS/Operating-Systems-Interrupts.html",
      "type": ["LearningResource", "PresentationDigitalDocument"],
      "name": "OS02: Interrupts"
    },
    {
      "id": "https://oer.gitlab.io/OS/Operating-Systems-Memory-I.html",
      "type": ["LearningResource", "PresentationDigitalDocument"],
      "name": "OS08: Virtual Memory I"
    }
  ]
}
}</script>
```

### Kontrollierte Vokabulare

Um Interoperabilität zu gewährleisten, ist die Verwendung eines kontrollierten Vokabulars bei einigen Metadatenattributen sinnvoll und wünschenswert.
Dabei ist zu beachten, dass ein Vokabular für den eigenen Service wesentlich elaborierter sein kann, als dasjenige, das für den Datenaustausch genutzt wird.
Unter Umständen stellt ein Vokabular den kleinsten gemeinsamen Nenner dar, auf den sich alle am Austausch interessierten Parteien einigen konnten.
Im AMB werden für verschiedene Attribute konkrete Vokabulare vorgeschlagen.
Um das Fach oder Thema zu beschreiben beispielsweise:

- [Hochschulfächersystematik](https://w3id.org/kim/hochschulfaechersystematik/scheme)
- [Schulfächer](http://w3id.org/kim/schulfaecher/)

Solche kontrollierten Vokabulare werden mit dem Standard [SKOS ("Simple Knowledge Organization System")](https://www.w3.org/TR/skos-primer/) publiziert.
Zur Hilfestellung gibt es eine deutschsprachige [Einführung in SKOS](https://w3id.org/kim/skos-einfuehrung/), die im Rahmen der KIM-Gruppe entwickelt wurde.

Zur einfachen Pflege und Publikation von SKOS-Vokabularen eignet sich [SkoHub Vocabs](https://github.com/skohub-io/skohub-vocabs), das selbst lokal aufgesetzt oder als Service unter https://skohub.io/ genutzt werden kann.


## Darstellung anderer Objekttypen als Lernressourcen

Die oben beschriebenen Verfahren lassen sich auch die Darstellung verschiedenster anderer Objekte übertragen.
Entsprechend eingebettete Daten finden sich auf vielen Webseiten, ob es um Rezepte, Kurse oder Autos geht:

- chefkoch.de
- udemy.com
- mobile.de
- ...

Bei schema.org liegen bereits eine Vielzahl von Typen und Attributen vor, die entsprechend genutzt werden können.
Wenn kein nutzbarer Typ oder keine nachnutzbaren Attribute gefunden wurden, können auch eigene entwickelt werden.

## Links

- [Vokabulare der OER-Metadatengruppe](https://wiki.dnb.de/display/DINIAGKIM/Wissenssammlung) (siehe unter Vokabulare)
- [OpenEduHub-Vokabular](http://w3id.org/openeduhub/vocabs/)
- [SkoHub](skohub.io): Tools zur Erstellung und Pflege von Vokabularen/einheitlichen Attributwerten
- [OER-Metadatengruppe](https://wiki.dnb.de/display/DINIAGKIM/OER-Metadatengruppe)
- [k12ocx](https://k12ocx.github.io/k12ocx-specs/): Projekt von Phil Barker über die Darstellung und Modellierung von Curricula und zugehörigen Contents
- [Herausforderungen für OER-Metadaten](https://kurzelinks.de/metadaten-fuer-oer) (Zusammenstellung von Jointly)



## Lizenzhinweis

<p xmlns:dct="http://purl.org/dc/terms/" xmlns:vcard="http://www.w3.org/2001/vcard-rdf/3.0#">
  <a rel="license"
     href="http://creativecommons.org/publicdomain/zero/1.0/">
    <img src="http://i.creativecommons.org/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
  </a>
  <br />
  To the extent possible under law,
  <a rel="dct:publisher"
     href="mailto:steffen.roertgen@gwdg.de">
    <span property="dct:title">Steffen Rörtgen</span></a>
  has waived all copyright and related or neighboring rights to
  <span property="dct:title">Wie meine Metadaten bereitstellen?</span>.
This work is published from:
<span property="vcard:Country" datatype="dct:ISO3166"
      content="DE" about="mailto:kontakt@steffen-roertgen.de">
  Deutschland</span>.
</p>
