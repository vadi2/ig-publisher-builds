# Optimised IG Publisher builds

Use the jar by copying it over `input-cache/publisher.jar` in the IG and running `_genonce.sh`. Don't run `_updatePublisher`, which replaces it with the official jar.

## publisher-3.0.0-optimised.jar

IG Publisher 3.0.0 built against core 7.0.1, with the build-time optimisations from the vadi2/org.hl7.fhir.core and vadi2/fhir-ig-publisher PR stacks rebased onto those releases. 3.0.0 already closes the files its HTML checker reads (HL7/fhir-ig-publisher#1391), so the stream-closing fix isn't needed.

sha256: `34f1bc11c5fd1a9c1d639ad5a8b11b4939073c09e8b8c99838d626c0dde796c1`

## publisher-2.3.4-optimised.jar

IG Publisher 2.3.4 built against core 6.10.4, with the same optimisations and the stream-closing fix from HL7/fhir-ig-publisher#1387.

sha256: `3d163683433f62d3faac436249b6513683126b224f734bb70aff4cf95fc26456`
