# DevFlow — Deployment Guide

## Overview

This document describes the basic deployment process for DevFlow.

The project follows a Git-based workflow where changes are developed on feature branches, reviewed through Pull Requests, and integrated into the `develop` branch.

## Deployment Workflow

```text
Feature Branch
      ↓
Development
      ↓
Commit
      ↓
Push
      ↓
Pull Request
      ↓
Code Review
      ↓
Merge
      ↓
develop
      ↓
Release
```

## Branches

* `main` — stable production version
* `develop` — integration branch
* `feature/*` — new features
* `fix/*` — bug fixes
* `release/*` — release preparation

## Basic Deployment Steps

### 1. Update the local repository

```bash
git switch develop
git pull origin develop
```

### 2. Create a feature branch

```bash
git switch -c feature/deployment-docs
```

### 3. Make the required changes

Update the project files and verify the changes locally.

### 4. Commit the changes

```bash
git add .
git commit -m "docs: add deployment guide"
```

### 5. Push the branch

```bash
git push -u origin feature/deployment-docs
```

### 6. Create a Pull Request

Open a Pull Request from `feature/deployment-docs` to `develop`.

The Pull Request should be reviewed before merging.

## Continuous Integration

GitHub Actions automatically runs the DevFlow CI workflow when changes are pushed to `develop` or submitted through a Pull Request.

The CI verifies the required project structure before accepting the changes.

A successful CI run should display:

```text
DevFlow CI
✓ Validation successful
```

## Release

Stable versions are identified using Git tags.

Example:

```bash
git tag -a v0.1.0 -m "Release DevFlow v0.1.0"
git push origin v0.1.0
```

A GitHub Release can then be created from the tag.

## Deployment Checklist

Before a release:

* [ ] Changes are committed
* [ ] Pull Request has been reviewed
* [ ] CI is successful
* [ ] `develop` is synchronized with GitHub
* [ ] Version tag is created
* [ ] GitHub Release is published

## Conclusion

DevFlow uses a structured Git and GitHub workflow to keep development organized, reviewed, and automatically validated before release.
