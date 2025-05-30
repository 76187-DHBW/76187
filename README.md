# Strömungsmaschinen Pumpenanalyse

## Indentifikationsnummer
76187

## Projektbeschreibung

Dieses Repository enthält das Projekt für die **Strömungsmaschinen-Vorlesung** an der **DHBW Karlsruhe**. Ziel des Projekts ist es, das Betriebsverhalten einer Wasserpumpe anhand vorliegender Messdaten und Herstellerangaben zu analysieren. Dabei werden der Energieverbrauch sowie die Effizienz der Pumpe berechnet und ausgewertet.

## Projektkontext

Das Projekt untersucht eine Wasserpumpe in einer industriellen Umgebung. Die Messdaten, insbesondere der Volumenstrom, sind in der Datei `volume_flow_data.csv` gespeichert. Die Pumpe verfügt über einen Impellerdurchmesser von **264 mm**. Das Datenblatt des Herstellers liefert unter anderem die Förderhöhe (Pumpenkopf) in Abhängigkeit vom Volumenstrom.

## Anforderungen

- **Python 3.x**  
- **Jupyter Notebook** oder eine andere geeignete Python-Umgebung  
- Python-Bibliotheken: **pandas**, **numpy**, **scipy**, **matplotlib** (für Visualisierung)

## Aufgabenstellung

1. **Berechnung des Energieverbrauchs**  
   Abschätzung der gesamten zugeführten elektrischen Energie basierend auf Messdaten des Volumenstroms.

2. **Bestimmung der Pumpen-Effizienz**  
   Ermittlung der durchschnittlichen Effizienz als Verhältnis von hydraulischer Energie zu zugeführter elektrischer Energie.

3. **Berechnung der ungenutzten Energie**  
   Bestimmung der Energieverluste, also der Energie, die nicht in hydraulische Arbeit umgesetzt wird.

4. **Visualisierung**  
   Darstellung der zeitlichen Verläufe von Volumenstrom, hydraulischer Leistung, Eingangsleistung und Verlustleistung.

## Methodik

- **Datenverarbeitung**  
  Umrechnung des Volumenstroms von m³/h in m³/s, Berechnung der Zeitdifferenz zwischen Messpunkten und Interpolation der Förderhöhe anhand der Herstellerkennlinie.

- **Energieberechnung**  
  Berechnung der hydraulischen Leistung und der elektrischen Eingangsleistung, gefolgt von der Integration über die Zeit zur Bestimmung des Energieverbrauchs.

- **Effizienzberechnung**  
  Bestimmung der Pumpenwirkungsgrade durch das Verhältnis von hydraulischer Energie zu Eingangsenergie.

- **Visualisierung**  
  Erstellung von Plots zur anschaulichen Darstellung der wichtigsten Kennwerte über den Messzeitraum.

 ## Formeln und Berechnungen

- **Umrechnung Volumenstrom**  
  Q = V / t  (Volumenstrom in m³/s)  
  Der Volumenstrom wird aus den Messdaten in m³/h umgerechnet in m³/s durch Division durch 3600.

- **Hydraulische Leistung**  
  P_hydr = ρ * g * Q * H  
  
  mit  
  ρ = Dichte des Mediums (969 kg/m³),  
  g = Erdbeschleunigung (9,81 m/s²),  
  Q = Volumenstrom (m³/s),  
  H = Förderhöhe in Meter (aus Herstellerkennlinie interpoliert).

- **Eingangsleistung**  
  Die elektrische Eingangsleistung P_input wird aus Herstellerdaten in Abhängigkeit vom Volumenstrom interpoliert.

- **Energie**  
  Die zugeführte und hydraulisch umgesetzte Energie werden durch Integration der Leistungen über die Zeit berechnet:  
  E = Σ P * Δt

- **Wirkungsgrad**  
  η = (E_hydraulisch / E_input) * 100 %

## Visualisierung und Mittelwertbildung

Für die Visualisierung der zeitlichen Verläufe wird ein gleitender Mittelwert (Rolling Mean) verwendet, um Messrauschen zu reduzieren und Trends besser sichtbar zu machen. 

Der Mittelwert über ein kleines Fenster (z.B. 5 Messpunkte) glättet kurzfristige Schwankungen, die durch Messfehler oder kurzzeitige Störungen entstehen können, ohne die generelle Dynamik des Systems zu verfälschen. So werden aussagekräftigere Kurven für die hydraulische Leistung, Eingangsleistung und Verlustleistung erzeugt, die eine bessere Interpretation der Pumpenleistung über den Messzeitraum erlauben.

---
