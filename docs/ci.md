# CI
PRs and merge queues use one Depot Linux checkout/toolchain for build, race
tests, coverage, examples, vulnerability checks and lint. The previous three
shared build calls repeated root vulnerability scans and three-OS setups;
separate coverage and lint workflows are removed.
Weekly/manual compatibility runs retain Linux, macOS and Windows builds/tests
for the Go versions declared by the root and examples modules. The routine
job uses stable Go. Native platform regressions therefore no longer block
each PR. macOS uses depot-macos-latest.
Upstream configuration-sync workflows are removed; repository configuration
is maintained through ordinary reviewed changes. Example module maintenance
and tagged releases remain. The shared release implementation is local and
attributed to its exact upstream commit so its runner cannot silently switch
to GitHub or Blacksmith. Existing signing, SBOM and publishing steps remain.
