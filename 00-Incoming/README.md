# 00-Incoming

Staging zone for files dropped before ingestion. Files here are waiting to be processed.

## Process

1. Read the file and extract all relevant information
2. Route each piece to its target (see Ingestion Routing in CLAUDE.md)
3. Move the original to the ingestion archive

This folder should be empty when there's nothing to process.
