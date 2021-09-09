# Minimal test case reproducing [snyk test incorrectly returns status 0 or 1 when "Failed to get dependencies" error occurs](https://github.com/snyk/snyk/issues/2242)

## Reproduction steps

Clone this repository then, from the cloned path:
1. `npm install snyk@latest -g`
2. `snyk test --all-projects && echo $?`

### Actual results
```
$ snyk test --all-projects && echo $?
✗ 1/3 potential projects failed to get dependencies.
/home/candrews/projects/snyk-test/react-app/package.json:
  Missing node_modules folder: we can't test without dependencies.
Please run 'npm install' first.

Testing /home/candrews/projects/snyk-test...

Organization:      candrews
Package manager:   gradle
Target file:       build.gradle
Project name:      snyk-test
Open source:       no
Project path:      /home/candrews/projects/snyk-test
Licenses:          enabled

✔ Tested 45 dependencies for known issues, no vulnerable paths found.

Next steps:
- Run `snyk monitor` to be notified about new related vulnerabilities.
- Run `snyk test` as part of your CI/test.

-------------------------------------------------------

Testing /home/candrews/projects/snyk-test...

Organization:      candrews
Package manager:   npm
Target file:       package-lock.json
Project name:      package.json
Open source:       no
Project path:      /home/candrews/projects/snyk-test
Licenses:          enabled

✔ Tested 3 dependencies for known issues, no vulnerable paths found.

Next steps:
- Run `snyk monitor` to be notified about new related vulnerabilities.
- Run `snyk test` as part of your CI/test.


Tested 2 projects, no vulnerable paths were found.

Exit status: 0
```

### Expected results
Same as the actual results, except ending with:
```
Exit status: 3
```
