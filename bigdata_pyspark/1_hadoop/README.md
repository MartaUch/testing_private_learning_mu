## Budowanie kontenerów i uruchamianie hadoop

## Hadoop MapReduce

## Opis

Hadoop MapReduce to model programowania służący do przetwarzania i generowania dużych zbiorów danych w sposób rozproszony. Wykorzystuje dwa główne etapy: **Map** (mapowanie) oraz **Reduce** (redukowanie).

## Struktura programu MapReduce

1. **Mapper** – przetwarza wejściowe dane na pary klucz-wartość.
2. **Reducer** – agreguje i przetwarza dane wyjściowe z mappera.
[Oficjalna dokumentacja MapReduce](https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html)
[Anatomia MapReduce](https://ercoppa.github.io/HadoopInternals/AnatomyMapReduceJob.html)

## Kroki:

1. Uruchamiamy Visual Studio Code oraz sklonowane repozytorium
2. Uruchamiamy wiersz poleceń (bash)
3. Uruchamiamy Linuxa
   ```
   wsl
   ```
4. Kierujemy się do odpowiedniej lokalizacji pliku docker-compose.yml (na zajęciach będziemy korzystać z kilku). Poruszamy się po strukturze plików korzystając z komendy `cd`.

   ```
   cd bigdata_pyspark\hadoop\MapReduce
   ```

5. Budowa kontenerów i uruchomienie hadoop

   ```
   # Budowanie wszystkich obrazów Dockera zdefiniowanych w pliku docker-compose.yml.
   docker-compose build

   # Uruchamianie wszystkich kontenerów z pliku docker-compose.yml w tle (detached mode)
   docker-compose up -d

   # Otwieranie interaktywnej powłoki Bash wewnątrz działającego kontenera o nazwie "hadoop"
   docker exec -it hadoop bash
   ```

6. Uruchom Hadoop w trybie lokalnym

   ```
   # Przechodzenie do katalogu instalacyjnego Hadoop w wersji 3.3.6
   cd hadoop-3.3.6
   
   # Uruchamianie przykładowego zadania MapReduce „wordcount”, które liczy wystąpienia słów w pliku data.txt i zapisuje wynik w katalogu output
   bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-3.3.6.jar wordcount data.txt output
   
   # Wyświetlanie listy plików znajdujących się w katalogu output, gdzie zapisano wyniki przetwarzania
   ls output
   
   # Wyświetlanie zawartości pliku wynikowego z liczbą wystąpień poszczególnych słów
   cat  output/part-r-00000

   ```