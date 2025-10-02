# Deployment Guide

## Automatic Deployment

This repository is configured with GitHub Actions for automatic deployment.

### How It Works

1. **On Push to Main**: When changes are pushed to the `main` branch, the CI/CD workflow automatically:
   - Builds the specification using Bikeshed
   - Validates the output
   - Publishes to the `gh-pages` branch

2. **On Pull Request**: When a PR is created, the workflow:
   - Builds and validates the specification
   - Ensures no breaking changes

### Workflow Configuration

The deployment is configured in `.github/workflows/build-validate-publish.yml`:
- Uses `w3c/spec-prod@v2` action
- Publishes to `gh-pages` branch
- Runs on Ubuntu 22.04

### Viewing the Published Spec

After deployment, the specification is available at:
- **Editor's Draft**: https://w3c.github.io/webauthn/
- **Official W3C Draft**: https://www.w3.org/TR/webauthn/

### Manual Deployment (if needed)

If manual deployment is required:

1. Install Bikeshed:
   ```bash
   pip3 install bikeshed && bikeshed update
   ```

2. Build the specification:
   ```bash
   bikeshed spec
   ```

3. The output will be `index.html`

### Deployment Checklist

Before merging to main:
- [ ] All tests pass
- [ ] Specification builds without errors
- [ ] No breaking changes introduced
- [ ] PR has been reviewed and approved

### Monitoring Deployment

- Check GitHub Actions tab for deployment status
- View build history at: https://github.com/w3c/webauthn/actions
- Monitor the W3C WebAuthn Blog for updates: https://www.w3.org/blog/webauthn/

## Troubleshooting

If deployment fails:
1. Check the Actions tab for error logs
2. Verify Bikeshed syntax in `index.bs`
3. Ensure all required metadata is present
4. Check for syntax errors or validation issues

## Support

For questions or issues:
- Review existing issues: https://github.com/w3c/webauthn/issues
- Contact the W3C WebAuthn Working Group
