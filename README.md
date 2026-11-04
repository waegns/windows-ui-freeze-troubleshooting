# Windows UI Freeze Troubleshooting Lab

## Overview

This project documents a real-world Windows 11 issue where mouse input intermittently failed due to a UI freeze.

## Problem

After creating a network share using a direct IP path, the system experienced:

* UI freezing
* Mouse clicks not registering
* Temporary recovery after lock/unlock

## Root Cause

Explorer.exe became unresponsive due to blocking network calls to an unstable SMB path.

## Fix

* Removed network shortcut
* Cleared network sessions (`net use * /delete`)
* Restarted Explorer

## Skills Demonstrated

* Windows 11 troubleshooting
* Network share debugging (SMB behavior)
* Process isolation (Explorer.exe)
* Structured problem solving (isolate the change, test, fix, verify)

## Files

* [incident-report.md](incident-report.md): timeline and symptoms
* [root-cause-analysis.md](root-cause-analysis.md): technical breakdown
* [commands.md](commands.md): commands used

## Outcome

System stabilized and issue resolved.

