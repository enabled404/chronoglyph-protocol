# ChronoGlyph Protocol - Symbol Legend & Syntax Guide

Version: 0.1.0
Last Updated: 2025-05-31

## 1. Introduction

This document defines the symbols, syntax, and structural conventions of the ChronoGlyph Protocol. It is the authoritative reference for encoding and decoding documents using this system. The protocol is designed to be extensible and context-aware, allowing for nuanced representation of complex texts.

## 2. File Structure

A ChronoGlyph Protocol file (`.cgp`) generally follows this structure:

1.  **Preamble:**
    * Format: `⟨ChronoGlyph∞[param1:value1, param2:value2, ...]⟩`
    * Mandatory Parameters:
        * `v`: Protocol version (e.g., `0.1.0`).
        * `doc`: Unique document identifier (e.g., `US-DoI-1776`).
        * `ts`: Encoding timestamp (ISO 8601 format, e.g., `20250531T1800Z`).
    * Optional Parameters:
        * `enc`: Encoder identification (e.g., `user@example.com`).
        * `∇` or `hash`: Integrity hash of the source document or encoding (e.g., `sha256-abcdef...`).
        * `lang`: Primary language of the source document (e.g., `en-US`).
2.  **Main Corpus:** Composed of one or more Sections.
3.  **Epilogue:**
    * Format: `⟨/ChronoGlyph∞⟩`

## 3. Sections

Sections are the primary organizational units within the main corpus.

* Format: `◉SECTION_IDENTIFIER≡{ ...content... }`
* `SECTION_IDENTIFIER`: A unique uppercase string (e.g., `LEXICON`, `PREAMBLE`, `GRIEVANCES`). Standard identifiers are recommended for common document parts (see Section 8).
* Content within `{...}` follows the syntax rules defined below.

## 4. Core Syntax Elements

* **Assignments/Definitions:** `symbol = definition` or `label: expression`
    * Used extensively in `◉LEXICON≡` sections.
    * Example: `♔ = (Ε:monarch, name:"King George III")`
    * Example: `right_to_abolish: ∀(Ε:government, Π:destructive_of_ends) → Ε:people ⇒ Π+:alter_or_abolish(Ε:government)`
* **Expressions:** Combinations of symbols, literals, operators, and function-like structures.
* **Lists/Collections:** `[item1, item2, item3]`
    * Example: `inalienable_rights: [Α:life, Α:liberty, Α:pursuit_of_happiness]`
* **Grouping:** `(...)` for logical grouping and defining complex objects/tuples.
* **Literals:**
    * Strings: `"quoted text"` (double quotes).
    * Numbers: `1776`, `0.75`.
    * Booleans: `true`, `false`.
* **Comments:** `// This is a comment` (lines starting with `//` are ignored by parsers).

## 5. Symbol Categories & Notation

Symbols are the building blocks of meaning. They are often single characters or short mnemonics.

### 5.1. Primary Types (Prefix Notation)

* **`Ε:` (Entity):** Concrete or abstract nouns, actors, objects, concepts.
    * Examples: `Ε:people`, `Ε:king`, `Ε:government`, `Ε:law`, `Ε:right`, `Ε:God`
* **`Α:` (Attribute/Quality):** Properties, states, adjectives, adverbs describing qualities.
    * Examples: `Α:equal`, `Α:free`, `Α:just`, `Α:necessary`, `Α:unalienable`, `Α:destructive`
* **`Π:` (Process/Action/Event):** Verbs, actions, occurrences.
    * Examples: `Π:create`, `Π:declare`, `Π:secure`, `Π:obstruct`, `Π:suffer`, `Π:petition_for_redress`
* **`Σ:` (Structural/Logical Operator):** Connectives, quantifiers, modal operators.
    * Examples: See Section 6.
* **`ΛΞ:` (Lexical Token):** User-defined symbols representing specific terms from the source text, usually defined in `◉LEXICON≡`.
    * Example: `ΛΞ:tyranny` (if 'tyranny' is a key defined term). Often, these are used directly if their meaning is clear or globally defined.

### 5.2. Common Pre-defined Symbols (Illustrative - expand as needed)

*(This list should be significantly expanded for a full protocol)*

* **Entities (Ε):**
    * `Ε:self`: Themselves, oneself.
    * `Ε:creator`: A creator entity.
    * `Ε:world`: The world, mankind.
    * `Ε:nature`: Nature.
* **Attributes (Α):**
    * `Α:sacred`: Sacred.
    * `Α:humble`: Humble.
    * `Α:transient`: Light or transient.
* **Processes (Π):**
    * `Π:assume`: To assume or take on.
    * `Π:endow`: To be endowed with.
    * `Π:institute`: To institute or establish.
    * `Π:derive`: To derive from.
    * `Π:abolish`: To abolish.
    * `Π:pledge`: To pledge.

### 5.3. Symbol Modifiers (Suffixes)

* `⁺` (Superscript Plus): Denotes inherent, positive, or augmented quality/quantity.
    * Example: `Α:rights⁺` (inherent/unalienable rights).
* `⁻` (Superscript Minus): Denotes negative, reduced, or deprived quality/quantity.
* `*` (Asterisk): Denotes all instances or universal application.
* `!` (Exclamation Mark): Denotes emphasis or strong assertion.

## 6. Structural & Logical Operators (Σ:)

* **`→` (Implies/Leads To):** Logical implication, causal link, sequence.
* **`↔` (Equivalent To):** Logical equivalence.
* **`⇒` (Entails/Results In):** Stronger implication, often used for rights or duties stemming from a condition.
* **`∧` (And):** Logical conjunction.
* **`∨` (Or):** Logical disjunction.
* **`¬` (Not):** Logical negation.
* **`∀(...)` (For All):** Universal quantifier. Scope is defined by parentheses.
    * Example: `∀(Ε:person) → ...`
* **`∃(...)` (There Exists):** Existential quantifier.
    * Example: `∃(Α:right) such_that ...`
* **`∴` (Therefore/Thus):** Introduces a conclusion.
* **`∵` (Because/Since):** Introduces a premise or reason.
* **`⊛` (Derives From / Based On):** Indicates source or foundation.
    * Example: `Ε:just_powers ⊛ Σ:consent_of(Ε:governed)`
* **`:=` (Is Defined As):** Stronger than `=`, often for axiomatic definitions.

## 7. Enhanced Features

### 7.1. Contextual Semantic Modifiers

These operators modify the interpretation of adjacent symbols or expressions.

* **`«focus»...«/focus»`**: Delimits the primary semantic focus of an expression.
    * Example: `«focus»Ε:king«/focus» Π:refused_assent_to(Ε:laws)` (The king's refusal is the main point).
* **`¿causal?~`**: Prefixes a symbol or expression to mark it as a direct causal factor or precondition.
    * Example: `¿causal?~(Α:long_train_of_abuses) → Π:reduce_under_despotism`
* **`§temporal(...)`**: Qualifies an action or state with a specific temporal aspect.
    * Defined aspects: `present_static`, `present_continuous`, `past_simple`, `past_continuous`, `future_declarative`, `future_intent`, `habitual`.
    * Example: `Ε:king §temporal(past_continuous) Π:obstruct(Ε:justice)`
* **`§modal(...)`**: Qualifies an expression with a modal aspect.
    * Defined aspects: `necessary`, `possible`, `obligatory`, `permissible`.
    * Example: `§modal(necessary) Π:dissolve_political_bands`

### 7.2. Inline Rich Metadata (`{μ:...}`)

Provides a way to embed annotations directly within the encoding.

* Format: `{μ:key1="value1", key2=value2, ...}`
* Values must be valid literals (strings, numbers, booleans).
* Common Keys:
    * `note`: A free-text explanatory note.
    * `ref_id`: An identifier linking to an external ontology, definition, or another part of the document (e.g., `wikidata_Q123`, `concept_equality_v1`).
    * `confidence`: A numerical value (e.g., 0.0 to 1.0) indicating the encoder's confidence in the interpretation.
    * `version`: Version of a concept or interpretation.
    * `source_text_ref`: A specific page, line, or passage number from the original document.
    * `lang_orig`: Original language term if the symbol is a translation (e.g., `lang_orig="Dieu et mon droit"`).
* Example: `Α:rights⁺ {μ:note="Unalienable as per Locke's philosophy", ref_id="locke_treatise_s22", confidence=0.9}`

### 7.3. Layered Symbolism & Abstraction

* Define general symbols in the `◉LEXICON≡`.
* Refine them contextually using specific attributes or inline metadata.
* Use dot notation for hierarchical concepts if defined: `Ε:rights.civil`, `Ε:rights.natural`. (This requires clear lexicon definitions).
* Alternatively, use parameterized symbols: `Ε:right(type:civil)`.

## 8. Standard Section Identifiers (Recommended)

* `◉LEXICON≡` or `◉DEF≡`: Definitions of symbols and terms specific to the document.
* `◉META≡`: Document-level metadata not fitting in the preamble (e.g., authorship, historical context).
* `◉PREAMBLE≡` or `◉INTRO≡`: The introductory section of the document.
* `◉PRINCIPLES≡` or `◉AXIOMS≡`: Core principles, truths, or philosophical underpinnings.
* `◉ARGUMENT≡`: Main body of arguments or reasoning.
* `◉GRIEVANCES≡` or `◉CHARGES≡`: List of complaints or charges.
* `◉ATTEMPTS_REDRESS≡`: Description of attempts to seek resolution.
* `◉DENUNCIATION≡`: Denunciation of other parties.
* `◉CONCLUSION≡` or `◉DECLARATION≡`: The main concluding statement or declaration.
* `◉SIGNATORIES≡`: List of signatories or authors.
* `◉APPENDIX≡`: Supplementary material.
* `◉ESSENCE≡`: A highly condensed summary of the document's core message.

## 9. Extensibility

The ChronoGlyph Protocol is designed to be extensible:

* New symbols can be defined within a document's `◉LEXICON≡`.
* Proposals for new globally recognized symbols, operators, or structural elements should be made via the project's contribution process (see `CONTRIBUTING.md`).
* Domain-specific modules (e.g., `ChronoGlyph-Legal`, `ChronoGlyph-Philo`) can be developed by defining specialized sets of symbols and section types.

## 10. Versioning of this Legend

Changes to this Symbol Legend will be versioned. Always refer to the version specified in a document's preamble.
