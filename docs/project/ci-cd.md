# CI/CD Documentation

## Overview

## CI/CD Pipeline Overview
The CI/CD pipeline automates the process of building, testing, and release the application. It ensures that code changes are integrated and delivered efficiently and reliably.

## Pipeline Structure

### 1. Build Workflow

The project is built and tested across multiple platforms:
- Linux
- Windows
- MacOS (if applicable)

### 2. Testing Pipeline

Our testing pipeline includes:
- Unit Tests
- Build Validation
- Code Coverage Analysis

### 3. Deployment Stages

The deployment process includes:
- Verification of build artifacts
- Packaging for deployment
- Release deployment
- Copy of the code in a mirror repository

## Pipeline Triggers

The CI/CD pipeline is triggered on:
- Push to main branch
- Pull Request creation/update
- Manual trigger for deployments

## Environment Configuration

### Build Dependencies
- [CMake](https://cmake.org/)
- [VCPKG](https://vcpkg.io/en/)

## Deployment Process

### 1. Build
- **Objective**: Compile the source code.
- **Tools**: GitHub Actions.
- **Steps**:
    1. Checkout the code from the repository.
    2. Install the package manager and the dependencies
    3. Build the application.

### 2. Test
- **Objective**: Run automated tests to ensure code quality.
- **Tools**: GitHub Actions, Criterion.
- **Steps**:
    1. Run unit tests.

### 3. Release
- **Objective**: Cretae a new release when the code is merged to the main branch.
- **Tools**: GitHub Actions
- **Steps**:
    1. Create a zip file of the repository.
    2. Create windows executable file with nsis
    3. Create a new release on GitHub.

## Troubleshooting

Common pipeline issues and their solutions:
- Build failures
- Test failures
- Deployment issues