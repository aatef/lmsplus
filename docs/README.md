# LMS Plus SIS - Project Planning Docs

This folder contains the consolidated planning documentation for **LMS Plus SIS**, a unified platform that combines the feature sets of **Moodle**, **OpenEduCat**, and **Open edX** into a single Learning Management System (LMS) and School Information System (SIS).

## Mission

One product, one database, one codebase - delivering a complete school/college lifecycle: administration, academics, student management, online learning, assessments, grading, communication, and analytics.

## Documents

| # | Document | Description |
|---|----------|-------------|
| 1 | [Vision and Goals](01-vision-and-goals.md) | Product vision, goals, target users, non-goals |
| 2 | [Feature Matrix](02-feature-matrix.md) | Consolidated feature inventory from Moodle, OpenEduCat, Open edX |
| 3 | [Architecture](03-architecture.md) | High-level system architecture and tech stack |
| 4 | [Database Schema](04-database-schema.md) | Consolidated MySQL schema plan and migration strategy |
| 5 | [Roadmap](05-roadmap.md) | Phased implementation roadmap |

## Source Systems

- **Moodle** - open-source LMS, strongest in course activities, quizzes, grading, competency frameworks, badges, and plugins.
- **OpenEduCat** - Odoo-based education ERP/SIS, strongest in admissions, fees, attendance, library, hostel, transport, and finance.
- **Open edX** - MOOC platform, strongest in course authoring (Studio), video-based courses, XBlocks, and scalable learning delivery.

## Design Principles

1. **One consolidated schema** - a single MySQL database serving both LMS and SIS needs, with a canonical data model instead of "database merge" of three different schemas.
2. **Feature-first design** - every feature from the source systems is inventoried, prioritized, and mapped to modules.
3. **Progressive migration** - adopt the best conceptual model from each source (Moodle's activity model, OpenEduCat's ERP model, Open edX's course authoring) rather than copying raw SQL.
4. **Extensibility** - plugin/module architecture so future integrations are additive.

## Status

Planning phase. All docs are drafts pending review.
