# Optimised IG Publisher 2.3.4

`publisher-2.3.4-optimised.jar` is IG Publisher 2.3.4 built against core 6.10.4, with the build-time optimisations from the vadi2/org.hl7.fhir.core and vadi2/fhir-ig-publisher PR stacks and the stream-closing fix from HL7/fhir-ig-publisher#1387.

sha256: `3d163683433f62d3faac436249b6513683126b224f734bb70aff4cf95fc26456`

To use it, copy it over `input-cache/publisher.jar` in the IG and run `_genonce.sh`. Don't run `_updatePublisher`, which replaces it with the official jar.
