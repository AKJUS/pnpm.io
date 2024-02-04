# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Feb 4, 2024, 2:46 AM_ (_daily_ updated).

This benchmark compares the performance of npm, pnpm, Yarn Classic, and Yarn PnP (check [Yarn's benchmarks](https://yarnpkg.com/benchmarks) for any other Yarn modes that are not included here).

Here's a quick explanation of how these tests could apply to the real world:

- `clean install`: How long it takes to run a totally fresh install: no lockfile present, no packages in the cache, no `node_modules` folder.
- `with cache`, `with lockfile`, `with node_modules`: After the first install is done, the install command is run again.
- `with cache`, `with lockfile`: When a repo is fetched by a developer and installation is first run.
- `with cache`: Same as the one above, but the package manager doesn't have a lockfile to work from.
- `with lockfile`: When an installation runs on a CI server.
- `with cache`, `with node_modules`: The lockfile is deleted and the install command is run again.
- `with node_modules`, `with lockfile`: The package cache is deleted and the install command is run again.
- `with node_modules`: The package cache and the lockfile is deleted and the install command is run again.
- `update`: Updating your dependencies by changing the version in the `package.json` and running the install command again.

## Lots of Files

The app's `package.json` [here](https://github.com/pnpm/pnpm.io/blob/main/benchmarks/fixtures/alotta-files/package.json)

| action  | cache | lockfile | node_modules| npm | pnpm | Yarn | Yarn PnP |
| ---     | ---   | ---      | ---         | --- | ---  | ---  | ---      |
| install |       |          |             | 59s | 10.8s | 7.8s | 4.2s |
| install | ✔     | ✔        | ✔           | 1.5s | 1s | 5.1s | n/a |
| install | ✔     | ✔        |             | 7.2s | 2.6s | 5.4s | 1.4s |
| install | ✔     |          |             | 12.8s | 7.7s | 8s | 3.6s |
| install |       | ✔        |             | 12.3s | 5.5s | 5.5s | 1.4s |
| install | ✔     |          | ✔           | 1.7s | 2.3s | 7.3s | n/a |
| install |       | ✔        | ✔           | 1.5s | 1.1s | 4.9s | n/a |
| install |       |          | ✔           | 1.7s | 5.6s | 7.1s | n/a |
| update  | n/a | n/a | n/a | 10.8s | 4.7s | 6.2s | 3.4s |

<img alt="Graph of the alotta-files results" src="/img/benchmarks/alotta-files.svg" />