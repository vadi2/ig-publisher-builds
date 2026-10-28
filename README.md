# Optimised IG Publisher builds

Use the jar by copying it over `input-cache/publisher.jar` in the IG and running `_genonce.sh`. Don't run `_updatePublisher`, which replaces it with the official jar.

## Experimental faster builds

1. Copy the rapido jar over `input-cache/publisher.jar`.
2. Instead of running `./_genonce.sh`, start the publisher from the IG folder and leave it running:

   ```
   export JAVA_TOOL_OPTIONS="-Xms6g -Xmx12g -Dfile.encoding=UTF-8"
   java -jar input-cache/publisher.jar -ig . -rapido -watch
   ```
3. The first run is a full build. After that, every time you save a file in the IG, the publisher rebuilds only what changed. Don't run `_genonce.sh` or start a second watcher in the same folder.
4. A rebuild is done when `output/qa.json` is rewritten. The publisher deletes the file while it rebuilds.
5. Stop the watcher with Ctrl+C.

## publisher-3.0.2-SNAPSHOT-rapido.jar

IG Publisher 3.0.1 (the release plus the 3.0.2-SNAPSHOT version bump, 4ba5b0ae) built against core 7.0.2, with the vadi2/fhir-ig-publisher perf2 stack (perf2/all2, c19a2b47): faster `-rapido` differential builds, warm `-watch` rebuilds, page-only rebuilds when only pages change, Jekyll and watch dependency fixes, and non-ASCII page names, with the fixes for Rapido and watch mode on Windows, and watch mode failing on a temp folder it can't make. The input-cache workstream (ws7) isn't included.

Run it with `-rapido` for differential builds, and add `-watch` to rebuild on every change:

```
java -jar publisher.jar -ig . -rapido -watch
```

sha256: `838aa92226c9ff8eefd1ebe3153ec5053a7a5b28544c419fb2ea86676d1839b6`

## publisher-3.0.0-optimised.jar

IG Publisher 3.0.0 built against core 7.0.1, with the build-time optimisations from the vadi2/org.hl7.fhir.core and vadi2/fhir-ig-publisher PR stacks rebased onto those releases. 3.0.0 already closes the files its HTML checker reads (HL7/fhir-ig-publisher#1391), so the stream-closing fix isn't needed.

sha256: `34f1bc11c5fd1a9c1d639ad5a8b11b4939073c09e8b8c99838d626c0dde796c1`

## publisher-2.3.4-optimised.jar

IG Publisher 2.3.4 built against core 6.10.4, with the same optimisations and the stream-closing fix from HL7/fhir-ig-publisher#1387.

sha256: `3d163683433f62d3faac436249b6513683126b224f734bb70aff4cf95fc26456`
