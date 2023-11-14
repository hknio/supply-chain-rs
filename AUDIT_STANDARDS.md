# Rust Crate Auditing Standards for Blockchain Projects

## Why Standards Matter in Blockchain Auditing

In the scrutiny of third-party code within the blockchain realm, adherence to well-defined standards is crucial. These standards, succinctly described, serve as benchmarks guiding the evaluation of code alignment within the blockchain ecosystem. Drawing parallels to legal principles, these auditing criteria function as the "laws" governing blockchain code.

In the realm of blockchain security, Hacken assumes the role of maintaining and enforcing these auditing criteria. Functioning as a judge, Hacken determines whether a given code complies with or violates the established standards. This comparison highlights the nuanced interpretation among auditors, where differences in leniency and real-world experiences shape decision-making processes.

Ensuring the applicability of audits across diverse blockchain projects is paramount. Confidence in consistent assessments by different auditors for the same code is vital. In the blockchain context, these auditing standards act akin to "case law," instilling confidence through clarifying remarks, case studies, and stipulated processes. This ensures that under the guardianship of Hacken, blockchain projects adhere to a unified set of standards, reinforcing security and reliability in the blockchain space.

## Summary

Outlined below are the auditing criteria and the requirements for auditors in the context of blockchain projects. Contributors seeking criteria for auditing can refer to the table for guidance.

| **Criteria**                          | **Requires**                                      |
|---------------------------------------|---------------------------------------------------|
| [`crypto-safe`]                       | **Cryptography expertise** and **Rust expertise** |
| [`does-not-implement-crypto`]         | **Generalist SWE**                                |
| [`safe-to-run`]                       | **Generalist SWE**                                |
| [`safe-to-deploy`]                    | **Generalist SWE**                                |
| [`contains-unsafe`]                   | **Rust expertise**                                |

[`crypto-safe`]: #crypto-safe
[`does-not-implement-crypto`]: #does-not-implement-crypto
[`safe-to-run`]: #safe-to-run
[`safe-to-deploy`]: #safe-to-deploy
[`contains-unsafe`]: #contains-unsafe

## Common Criteria

### Cryptography

#### `crypto-safe`

Requires **Cryptography expertise** and **Rust expertise** 

Crates with this criteria contain implementations of cryptographic algorithms, reviewed by an expert and deemed acceptable. Cryptography is mission-critical, and a crate audited as crypto-safe is deemed suitable for use.

#### Guidelines

*   An expert must review cryptographic algorithms, ensuring their acceptability. Generalist SWEs and others without cryptographic expertise may not audit for this criteria.
*   Mere code comparison against reference pseudocode or another implementation is not acceptable.
*   Collaboration between a cryptography expert and a Rust language expert is recommended to verify implementation accuracy.

### `does-not-implement-crypto`

Requires **Generalist SWE**

Crates with this criteria do not implement cryptographic algorithms.

#### Criteria Guidelines

*   Generalist SWEs can determine if a crate contains cryptographic implementations.
*   Crates using cryptographic algorithms without implementing them may still be audited as `does-not-implement-crypto`.

## Deployment

### `safe-to-run`

Requires **Generalist SWE**

This criteria, integrated with cargo vet, describes a crate safe for compilation, testing, and running locally or in controlled automation.

#### Criteria Guidelines

*   Generalist SWEs can determine if a crate is safe to run.
*   Crates must not perform actions such as reading or writing data from sensitive parts of the filesystem, installing software, or connecting to untrusted network endpoints.
*   Misuse of system resources, like cryptocurrency mining, is strictly prohibited.

### `safe-to-deploy`

Requires **Generalist SWE**

This criteria, part of cargo vet, identifies a crate not introducing serious security vulnerabilities to production software exposed to untrusted input.

#### Criteria Guidelines

*   While no specific expertise is required, generalist SWEs must be familiar with all auditing criteria and standards.
*   Reviewers must assess all unsafe blocks and powerful imports, ensuring they are secure against manipulation.
*   Discretion is allowed but must be documented in the audit record's `notes` field.
*   This criteria is not a soundness review; see the "Soundness" group for soundness-related criteria.
*   Deployment requirements may vary across organizations.

### `contains-unsafe`

Requires **Rust expertise**

This criteria identifies a crate containing unsafe blocks. Unsafe blocks are a Rust language feature allowing the bypassing of Rust's safety guarantees. Unsafe blocks are often used to implement cryptographic algorithms or to interface with external libraries.

#### Criteria Guidelines

*   Unsafe blocks must be reviewed by a Rust language expert.
*   Unsafe blocks must be documented in the audit record's `notes` field.
*   Unsafe blocks must be used only when necessary and must be secure against manipulation.
