---
title: Roadmap
description: Planned features / improvements for future releases
published: true
date: 2020-08-22T18:22:23.470Z
tags: 
editor: markdown
---

This page list possible important features and refactoring ideas for future major versions.

> These are not set in stone and only serve as a discussion point.
{.is-warning}

[Suggest new features / improvements](https://requarks.canny.io/wiki)

# 2.x

## Authentication
- Account Linking
- CAS Module
- Map LDAP groups to Wiki.js groups
- Microsoft Account Module
- View As capability

## Editor
- ASCIIDoc Editor
- Asciinema Support
- API Editor *(REST/GraphQL)*
- Autosave Draft
- Blog Editor
- Create Redirect Page
- Columns for content
- Commit message upon saving
- Draw&#46;io Diagrams Integration for Visual Editor
- Directory Page (List children)
- Inline Templates (Content Transclusion)
- Paste images into editor
- Previous / Next Links

## Media Assets
- Compress Images
- Edit Image (crop, resize, filters, etc.)
- Edit / Delete Folders
- Search Assets

## Page Management
- Batch rename / move pages
- Bookmark / Collections
- Delete orphaned tags automatically
- Export to PDF
- Import Content
  - From Wikimedia
  - From DokuWiki
  - From Confluence
- Purge old history automatically
- Switch editor for an existing page
- Recycle Bin

## Site Administration
- Change Favicon
- Save Navigation configuration into storage
- Statistics / Reports
- Webhooks

## Storage
- Multi-git repository support
- IPFS Module
- Box, Dropbox, Google Drive, OneDrive Modules

## Theme / Layout
- Hide TOC block / Move to right
- Hide Last Edited By block

## User Interaction
- Page Rating
- Embed mode for Pages
- Messaging System

# 3.x

## Use PostgreSQL as sole database engine

The current implementation for database handling is done via Knex.js and Objection.js, which allows for various drivers to be used for PostgreSQL, MySQL, MariaDB, SQL Server and SQLite. While it offers broad compatibility for users, it also brings major limitations for the architecture and development in general:

- Many different configurations to support
- Some functions require different implementations based on the driver
- Some functions are simply not implemented in some database engines:
	- *Recursive Queries*
  - *Pub/Sub Notification*
  - *Advanced Search Capabilities*
- Some migrations can be complex (specifically MS SQL Server)

Supporting PostgreSQL as the only database engine in 3.x would greatly simplify development.

## Switch to a full SPA model for navigation

At the moment, only the administration area is using a SPA navigation model (switch views without reloading the page). Standard view pages don't use this model for easier SEO.

In 3.x, site-wide SPA should be implemented in addition to server-side rendering of page contents.

## Switch to Quasar Vue framework

- Allows for easier server-side rendering and mobile capabilities.
- Better components *(specifically the table component)*