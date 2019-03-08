# Policies for manifests

This document describes policies for structuring our manifests.

 * If members of the Fuchsia project do not have the authority to revert changes
   in a repository, that repository must be pinned to a specific git hash. This
   policy prevents changes in such a repository from breaking the Fuchsia build
   and having Fuchsia project members be unable to fix the build by reverting
   the offending change.

 * Repositories hosted on external servers, such has GitHub, should use a
   project with a `name` attribute of the following form:
   `external/<hostname>/path/to/repo`. This naming scheme ensures that multiple
   references to the same external repository have consistent manifest values.

 * Projects that contain non-standard licenses should use a `path` attribute
   that begins with `third_party/`. The current standard licenses used
   by the Fuchsia project are 3-clause BSD, Apache 2.0, and MIT.

## Modes of operation

Each repository operates in one of two modes:

 * _Tracking upstream_. When a repository is tracking upstream, the Fuchsia
   project is not the source of truth for the code in that repository. Instead,
   we incorporate updated versions of the code periodically from an upstream
   repository, typically controlled by another group of people (e.g., another
   open source project).

   When tracking upstream, we typically create a mirror of the repository in the
   `third_party` directory with the *same name as the upstream project* in order
   to ensure the availability of the code for the Fuchsia build. The `master`
   branch should point at the ref used by Fuchsia -- typically a version tag.
   Branches that exist in the upstream repo are present in our mirror, prefixed
   with `upstream/` (e.g., `foo` becomes `upstream/foo`).

   Any local modifications to the code (e.g., to integrate with the build or the
   platform) should be landed in the `master` branch. When we fetch upstream
   changes, we merge our `master` branch with upstream so that the `master`
   branch contains both the updated upstream code and our local modifications.

   In the Fuchsia parlance, third party repos that are _tracking upstream_ are
   NOT considered "forks".

 * _Source of truth_. When a repository is the source of truth, the Fuchsia
   project controls the code in the repository. Projects that originate with the
   Fuchsia project operate in this mode (i.e., because there is no upstream that
   could be tracked), but sometimes we will use another project as the starting
   point for a repository and create a *fork* of the original project. When we
   create a fork of an existing project, we pick a new name for our project to
   avoid confusion.

   A repository that is the source of truth might be in the `third_party`
   directory or it might not be in the `third_party` directory, depending on its
   license (e.g., because we used a project with a non-standard license as a
   starting point).
