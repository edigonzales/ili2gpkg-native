# ili2gpkg-native

Native Images von _ili2gpkg_ für Windows, macOS und Linux. Java wird nicht mehr benötigt. Die grafische Oberfläche wird nicht unterstützt.

```
./ili2gpkg --help
```

Für jede Version von _ili2gpkg_ gibt es einen Branch, z.B. `V_4_9_1`. Das Native Image wird als Zip-Datei unter https://github.com/edigonzales/ili2gpkg-native/releases veröffentlicht. Die Zahl nach dem Unterstrich entspricht der Buildnummer der Github-Action. Der main-Branch kann keine Releases machen.

## Develop

Siehe auch https://github.com/edigonzales/ili2pg-native

Auf einem Apple Silicon Rechner muss der Agent bereits mit einer gepatchten Version gestartet werden. Nur diese verwendet einen kompatiblen Sqlite-JDBC-Treiber. Das ili2db-Repo auschecken und im _build.gradle_ die Sqlite-Version updaten (3.39.3.0). Builden mit `gradle clean build ili2gpkgJar ili2gpkgBindist -x userdoc`. Gradle darf höchste Version 6.9 sein. 

```
java -agentlib:native-image-agent=config-output-dir=conf-dir -jar /Users/stefan/apps/ili2gpkg-4.9.0-aarch64/ili2gpkg-4.9.0.jar --dbfile fubar.gpkg --nameByTopic --defaultSrsCode 2056 --strokeArcs --models SO_ARP_Bauzonengrenzen_20210120 --doSchemaImport  --import /Users/stefan/Downloads/ch.so.arp.bauzonengrenzen_xtf/ch.so.arp.bauzonengrenzen.xtf
```


