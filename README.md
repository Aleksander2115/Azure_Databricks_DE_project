# End-to-End Azure Data Engineering Project: Sales Analytics Lakehouse

## O projekcie
Projekt przedstawia kompletną architekturę Data Lakehouse zbudowaną w chmurze Azure. Proces obejmuje automatyczną ingestję danych, transformację w architekturze Medalionu (Bronze -> Silver -> Gold) oraz monitorowanie błędów w czasie rzeczywistym.

## Technologie
* **Azure Data Factory**: Orkiestracja i Ingestia danych
* **Azure Databricks (Spark)**: Przetwarzanie danych (PySpark)
* **Azure Data Lake Storage Gen2**: Magazyn danych (Delta Lake)
* **Azure Logic Apps**: System alertów e-mail o błędach
* **Delta Lake**: Format przechowywania zapewniający transakcyjność ACID

## Architektura Projektu
1. **Bronze (Raw)**: Surowe dane CSV pobrane przez ADF Copy Activity
2. **Silver (Cleaned)**: Dane po procesie schema enforcement, usunięciu duplikatów, filtracji nulli i złączeniu tabel Orders i Details
3. **Gold (Analytics)**: Zagregowane widoki gotowe do raportowania

## Kluczowe Funkcjonalności
* **Schema Enforcement**: Wykorzystanie `StructType` w Sparku do zapewnienia spójności typów danych
* **Error Handling**: Implementacja mechanizmu "On-Failure" w ADF zintegrowanego z Webhookiem Logic Apps
* **Data Quality**: Czyszczenie danych (trimowanie znaków ukrytych, filtrowanie rekordów)
* **Deduplikacja**: Mechanizm usuwania duplikatów w tabelach nadrzędnych przed operacjami łączenia
