# Strömungsmaschinen Pumpenanalyse

## Persönliche Nummer
*76187*

## Projektbeschreibung

**Dieses Repository dokumentiert ein Projekt im Rahmen der Vorlesung „Strömungsmaschinen“ an der DHBW Karlsruhe.**
Ziel des Projekts ist es, das Betriebsverhalten einer Wasserpumpe auf Basis vorhandener Messdaten und Herstellerinformationen zu untersuchen.
Im Mittelpunkt stehen dabei die Berechnung und Analyse des Energieverbrauchs sowie der Wirkungsgrad der Pumpe.

## Projekthintergrund

**Im Rahmen dieses Projekts wird eine Wasserpumpe untersucht, welche in einer industriellen Umgebung eingesetzt wird.**
Die erfassten Messdaten – insbesondere der Volumenstrom – sind in der Datei *volume_flow_data.csv* gespeichert.
Die Pumpe besitzt ein Laufrad mit einem Durchmesser von *264 mm*.
Das zugehörige Herstellerdatenblatt stellt unter anderem die Förderhöhe (Pumpenkopf) in Abhängigkeit vom Volumenstrom zur Verfügung.

## Projekt-Anforderungen
 
Die Abgabe der Ausarbeitung erfolgt über dieses GitHub-Repository. In diesem werden das Python-Skript, sowie eine Beschreibung, welches den ausgearbeiten Code ergänzen und beschreiben soll. Das Skript diet zur Analyse und Auswertung der gegebenen Daten.

## Aufgabenstellung

1. In der **ersten Aufgabe** soll die insgesamt von der *elektrischen Pumpe aufgenommene Energie* abgeschätzt werden. Grundlage dafür sind die Volumenstromdaten aus der *CSV-Datei*.

2. Die **zweite Aufgabe** widmet sich der Ermittlung der *durchschnittlichen Effizienz der Pumpe*, also dem Verhältnis zwischen aufgenommener elektrischer Leistung und tatsächlich erbrachter hydraulischer Leistung.

3. In der **dritten Aufgabe** wird die Differenz zwischen elektrischer und hydraulischer Leistung über den gesamten Zeitraum berechnet, um die *ungenutzte Energie* zu bestimmen.

4. Abschließend sollen in der **vierten Aufgabe** aussagekräftige Visualisierungen erstellt werden, die das *Betriebsverhalten der Pumpe* veranschaulichen – beispielsweise durch Zeitreihen, Histogramme oder andere geeignete Diagrammformen.

## Erarbeitung des Projektes

1. Zunächst wird die *CSV-Datei* eingelesen, die Zeitstempel und Volumenstromwerte in m³/h enthält. Für die Berechnung der hydraulischen Leistung werden die zugehörigen Förderhöhen benötigt. Diese werden mithilfe von Kennlinienpunkten aus dem Datenblatt als Arrays definiert und anschließend interpoliert.

   Wichtige Konstanten hierbei sind:

   - Dichte des Mediums: **ρ = 969 kg/m³**
   - Erdbeschleunigung: **g = 9,81 m/s²**
   - Messintervall: **Δt = 60 s**
   - Wirkungsgrad der Pumpe: **η = 83,1 %**
     
   Mit der Formel: **"ρ · g · H · Q"** wird die hydraulische Leistung berechnet. Über den Wirkungsgrad lässt sich daraus die elektrische Energieaufnahme in kWh abschätzen.

2. Für **Aufgabe 2** wird der tatsächliche Pumpenwirkungsgrad berechnet. Dazu werden erneut Kennlinienpunkte aus dem Datenblatt als Arrays definiert und interpoliert. Anschließend wird der durchschnittliche Wirkungsgrad ermittelt. Auf Basis dieses Werts wird der tatsächliche Energieaufwand neu berechnet und zur Korrektur von Aufgabe 1 ausgegeben.
3. In **Aufgabe 3** wird die gesamte hydraulische Energie berechnet, indem die hydraulische Leistung über die Zeit aufsummiert wird. Anschließend wird sie mit der elektrischen Gesamtenergie aus Aufgabe 2 verglichen und die Differenz als ungenutzte Energie ausgegeben.
4. Für die **vierte Aufgabe** sollen mehrere sinnvolle Visualisierungen ausgegeben werden:

   Das *erste Diagramm* zeigt die Verlustleistung aufgetragen über die Zeit. Es wird durch dieses Diagramm schnell ersichtlich, wie viel Leistung zu bestimmten Zeitpunkten nicht für den Antrieb des Mediums benutzt wird, sondern anders umgesetzt wird. Hierbei könnte im Falle der Instandhaltung schnell ersichtlich werden, wann der Verschleiß der Maschine zu hoch ist.
   
   Im *zweiten Diagramm* wird der Volumenstrom über der Zeit aufgetragen. Diese Ansicht ist besonders wichtig, um Engpässe zu ermitteln oder abzuleiten. Es ist schnell einsichtig, wann die Maschine welchen Volumenstrom geliefert hat. Hierbei könnten nach einer umfassenden Analyse Verbesserungen vorgenommen werden.

   Im *dritten und letzten Schaubild* werden die **hydraulische** und die **elektrische Energie** zusammen dargestellt. Es zeigt die elektrische Leistungsaufnahme (magenta) und die hydraulische Leistungsabgabe (blau) der Pumpe im Vergleich. dieses Diagramm veranschaulicht das Verhältnis beider Größen zueinander.
---
