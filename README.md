## SFG Brewery BOM

Common BOM for SFG Beer Works Projects

# Release option 1

Add `-SNAPSHOT` if we want to deploy to the snapshot repository (e.g. `<version>0.1.0-SNAPSHOT</version>`, otherwise `<version>0.1.0</version>`). Then run the deploy-command with the defined `ci-cd` profile:
```
mvn clean deploy -Pci-cd
```

# Release option 2

This only works with the `-SNAPSHOT`, that must be in sync with the remote repository. Then it automatically creates the release version, and bumps the local version to next _SNAPSHOT_. Steps:

1. Define snapshot version, e.g. `<version>1.0.3-SNAPSHOT</version>`
2. Commit changes and push to GitHub repository
3. Execute `mvn clean release:prepare -P ossrh`, and accept the defaults:
   - Release version: `1.0.3`
   - SCM release tag or label: `mssc-brewery-bom-1.0.3`
   - New development version: `1.0.4-SNAPSHOT`
4. Execute `mvn release:perform -P ossrh`