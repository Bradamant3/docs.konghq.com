[![Netlify Status](https://api.netlify.com/api/v1/badges/ae60f2a4-488e-4771-b24a-c26badc5f45d/deploy-status)](https://app.netlify.com/sites/kongdocs/deploys)

# Jennifer's fork of Kong's public docs site

THIS README IS FOR THE FORK ONLY.

N.B. DO NOT MERGE ANYTHING FROM THIS FORK TO UPSTREAM. 

Created fork to explore options for:

- version management with branches
- single-sourcing content for OSS and Enterprise Gateway

# Building the docs

Assume that local development can happen just like upstream. TODO TEST THIS.

N.B. NETLIFY NOT CONFIGURED TO BUILD THIS REPO. TODO: 

- FIGURE OUT HOW TO TEST
- GET DNS RECORD UPDATED FOR UPSTREAM (CAN WE TEST THIS TOO?)

## Develop Locally with Docker

```
make install-prerequisites
```

>
```bash
make develop
```

### Running a Local Build with Docker

Install tools:
```
make install
```

Run the build:
```
make run
```

Check the build output at http://localhost:3000.

### Testing Links with Docker

```
make check-links
```

## Develop Locally without Docker

### Prerequisites

- [node and npm](https://www.npmjs.com/get-npm)
- [yarn](https://classic.yarnpkg.com)
- [gulp](https://gulpjs.com/docs/en/getting-started/quick-start/)
- [Bundler](https://bundler.io/) (< 2.0.0)
- [Ruby](https://www.ruby-lang.org) (>= 2.0, < 2.3)
- [Python](https://www.python.org) (>= 2.7.X, < 3)

### Install

>
```bash
gem install bundler
npm install
```

### Running

>
```bash
npm start
```

# Versioning the docs

IN THIS FORK ONLY:

Versions live in branches. Branched version sets are determined by Gateway versions. Plan for other Kong products/components:

- KIC versions will eventually show up only in install/deploy content for Gateway. Concepts and refdocs will remain, but unversioned (going forward only, we won't backport this approach).
- decK is currently unversioned. Recommend leaving it that way, consider seriously incorporating content into main Gateway docs instead of documenting as a separate thing, but we can iterate on this one.
- Mesh will have to go along with Gateway -- we'll update to latest on main without versioned folder, work on aligning Mesh versions/Gateway support. This one needs more thought/work.

## How it works for the build (to be set up)

Going forward, work happens against main in the public repo (or against main in the private repo if for new features -- the public/private sync for releases remains the same as before).

(Another option is to create a release branch in the public repo for upcoming features, work against that branch, then merge to main on release. But this approach makes all docs work public, and is probably not going to fly with PM.)

When a _new_ release is cut, main becomes docs/version-x (major version only? this would be ... clearest perhaps? TODO DISCUSS), that branch is published _for the last time_ and becomes static. We accept no PRs against it, only against main. Work on docs improvements continues on the public main branch, and on new feature docs on the private main branch.

See [the single-sourcing google doc](https://docs.google.com/document/d/1siPcbOhyfVmLwn-sE9kdjAcCaPLxPG2kVObv_QmDAIU/edit#heading=h.ogfgl5ndxtt9) for discussion of the ongoing manual work required to maintain this approach. 

(If you're a community member who stumbles on this fork, note that the google doc is currently shared only with Kong folks. See the Kubernetes docs repo for an example of the approach we're considering.)


