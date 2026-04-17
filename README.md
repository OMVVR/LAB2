# 📱 Rooting Android - Laboratoire de Sécurité Mobile

**Course:** Mobile Application Security  
**Analyst:** Omar Haouani  
**Environment:** Android Virtual Device (AVD)  
**Date:** March 2026

---

## 📋 Table of Contents

1. [Introduction](#introduction)
2. [Environment Setup](#environment-setup)
3. [Root Privileges Acquisition](#root-privileges-acquisition)
4. [Target Application Deployment](#target-application-deployment)
5. [Functional Test Cases](#functional-test-cases)
6. [Android Security Fundamentals](#android-security-fundamentals)
7. [Verified Boot Mechanism](#verified-boot-mechanism)
8. [Rooting Definition](#rooting-definition)
9. [Risk Analysis](#risk-analysis)
10. [OWASP Standards](#owasp-standards)
11. [Cleanup and Reset](#cleanup-and-reset)
12. [Commands Summary](#commands-summary)
13. [Checklist](#checklist)
14. [Resources](#resources)

---

## Introduction

This practical work examines the impact of rooting on the Android ecosystem.

**Conduct Rules:**
- Exclusive use of a dedicated test environment
- Fictitious data only
- No interaction with external systems

---

## Environment Setup

| Element | Detail |
|---------|--------|
| Environment Type | Android Virtual Device (AVD) |
| Simulated Device | Pixel 6 |
| System Version | Android 36 (API 36) |
| Architecture | Google APIs x86_64 |
| Instance | rooted_avd |

### Connectivity Verification

![ADB Connection](5.png)

---

## Root Privileges Acquisition

| Command | Result |
|---------|--------|
| `adb shell id` | uid=0(root) gid=0(root) |
| `ro.boot.verifiedbootstate` | enforcing |
| `ro.boot.veritymode` | enforcing |
| `ro.boot.vbmeta.device_state` | enforcing |

![ADB Root Commands](2.png)

---

## Target Application Deployment

The test application presents a form with the following fields:
- Identity (First and Last Name)
- Email address
- Phone number
- Postal address
- City/Locality

### Empty Form

![Empty Form](3.png)

### Filled Form

Data entered: **Omar Haouani**, **0600712917**

![Filled Form](4.png)

---

## Functional Test Cases

### Scenario 1 - Interface Access
The application launches and displays the form without errors.

### Scenario 2 - Data Entry and Submission
Data entered: Omar Haouani, 0600712917, then submitted.

### Scenario 3 - Data Processing
The system processes the submission without anomalies.

---

## Android Security Fundamentals

1. **Application Isolation**: Each application operates in a confined space without interaction with other programs.

2. **Permission Management**: Access to sensitive resources requires explicit user validation.

3. **Kernel Protection**: The operating system preserves the integrity of critical components.

**Note:** Obtaining root privileges neutralizes these three mechanisms.

---

## Verified Boot Mechanism

### Verified Boot
Ensures that the executed system corresponds to the original version from the manufacturer.

![Fastboot Verification](6.png)

---

## Rooting Definition

Rooting consists of acquiring superuser rights (uid=0) on an Android device. This action modifies the security model by disabling application isolation and permission controls. In a laboratory environment, this configuration allows analyzing the internal behavior of applications. A complete reset after each session is mandatory.

---

## Risk Analysis

| # | Risk | Consequence |
|---|------|-------------|
| 1 | System integrity alteration | Non-representative results |
| 2 | Increased attack surface | Exposure to external threats |
| 3 | Sensitive data exposure | Confidentiality violation |
| 4 | Functional instability | Non-reproducible tests |
| 5 | Personal/test account mixing | Information leakage |
| 6 | Incomplete cleanup | Data persistence |
| 7 | Lack of network isolation | Unintentional interactions |
| 8 | Insufficient traceability | Non-reproducibility |

---

## OWASP Standards

### STORAGE-1 Requirement
Sensitive information must be protected by encryption. Clear text storage is prohibited.

### NETWORK-1 Requirement
Exchanges must use TLS with certificate validation.

---

## Cleanup and Reset

![Wipe Commands](7.png)

---

## Commands Summary

| Command | Purpose |
|---------|---------|
| `adb devices` | Verify connection |
| `adb shell id` | Check privileges |
| `adb shell getprop ro.boot.verifiedbootstate` | Verified Boot status |
| `fastboot getvar avb_boot_state` | AVB status |
| `adb emu avd wipe-data` | Complete cleanup |

---

## Checklist

- [x] Dedicated workspace created
- [x] APK signature verified
- [x] SHA-256 hash calculated for traceability
- [x] JADX decompilation completed
- [x] Manifest and resources analyzed
- [x] Verification code identified
- [x] Sensitive keys and data extracted
- [x] DEX to JAR conversion completed
- [x] Tools comparison performed
- [x] Recommendations written
- [x] Workspace cleaned up

---

## Resources

- [Android Security Documentation](https://source.android.com/docs/security)
- [Verified Boot](https://source.android.com/docs/security/features/verifiedboot)
- [AVB](https://source.android.com/docs/security/features/verifiedboot/avb)
- [OWASP MASVS](https://mas.owasp.org/MASVS)
- [OWASP MASTG](https://mas.owasp.org/MASTG)

---


