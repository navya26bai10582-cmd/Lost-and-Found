# Lost and Found Item Module

## Overview

This module manages lost and found reports in a student system. It supports reporting, browsing, claiming, editing, and closing items. Item records are stored through the database helpers, and changes are added to the history log.

## Features

- Create Lost or Found reports with a generated ID (`ITM001`, `ITM002`, ...).
- View all reports or only open Lost/Found reports.
- Claim an open report for a registered student.
- Update the description and location of an active report.
- Close an active report without a claim.
- Record report, claim, update, and close events in the audit history.

## Main functions

| Function | Purpose |
|---|---|
| `report_item()` | Collects report details, checks reporter registration, saves the record, and logs the event. |
| `view_all_items()` | Displays every item report. |
| `view_lost_items()` / `view_found_items()` | Displays open reports of the selected type. |
| `claim_item()` | Marks an eligible report as claimed by a registered student. |
| `update_item()` | Changes an active report's description and location. |
| `close_report()` | Closes an active report. |
| `generate_item_id()` / `find_item()` | Generates the next ID and finds an item by ID, case-insensitively. |

## Data and dependencies

An item record contains: item ID, name, type, description, location, report date, reporter student ID, estimated value, and status. The module depends on `database` for storage, `input_utils` for validated input and prompts, `student_module` for registration checks, `history_module` for audit logging, and `config` for item types and status constants.

## Status rules

Only open items can be claimed, updated, or closed. Claiming requires a registered student. Closed and claimed reports are treated as final and cannot be changed through these operations. Reporters must be registered before a new item can be saved.

