<!-- cSpell:ignore docsy hugo userguide -->

# How to Contribute

We'd love to accept your patches and contributions to this project. There are
just a few small guidelines you need to follow.

## Contributor License Agreement (CLA)

Contributions to this project must be accompanied by a Contributor License
Agreement. You (or your employer) retain the copyright to your contribution;
this simply gives us permission to use and redistribute your contributions as
part of the project. Head over to <https://cla.developers.google.com/> to see
your current agreements on file or to sign a new one.

You generally only need to submit a CLA once, so if you've already submitted one
(even if it was for a different project), you probably don't need to do it
again.

## Code reviews

All submissions, including submissions by project members, require review. We
use GitHub pull requests for this purpose. Consult
[GitHub Help](https://help.github.com/articles/about-pull-requests/) for more
information on using pull requests.

## Community Guidelines / Code of conduct

This project follows
[Google's Open Source Community Guidelines](https://opensource.google.com/conduct/).

## Student contributions

Docsy welcomes contributions from students. However, we cannot guarantee that
PRs will be merged within any specific time frame. We ask that instructors _not_
create assignments requiring students to have PRs merged into the project. We
will not merge PRs solely to satisfy any class assignments.

## How to contribute

See the [contribution guidelines][] in the Docsy user guide.

## Publishing a release

These notes are WIP for creating a **release (v0.X.Y)** from a local copy of the
repo.

1.  **Change directory** to your local Docsy repo.
2.  **Create or update a [CHANGELOG](CHANGELOG.md) entry** for v0.X.Y. The
    section should provide a brief summary of breaking changes using the section
    template at the end of the file. (Note that change details are autogenerated
    by GitHub in a later step.)
3.  **Update Docsy version** to v0.X.Y for:
    - `version` key in [package.json](package.json)
    - `version` key in [userguide/hugo.yaml][]
4.  Run `npm install` to have vendor assets and [go.mod](go.mod) updated.
5.  **Submit a PR with your changes**, using a title like "Release v0.X.Y
    preparation".
6.  **Get PR approved and merged**.
7.  **Pull in `main`** to get the last PR.
8.  **Ensure** that you're:
    - On the default branch, `main`
    - At the commit that you want to tag as v0.X.Y
9.  **Create tags** for v0.X.Y:

    ```sh
    REL=v0.X.Y
    git tag $REL
    ```

10. **Push the new tags** to the main repo, which is named `upstream` in the
    following example:

    ```console
    $ git push upstream $REL
    ...
    * [new tag]         v0.X.Y -> v0.X.Y
    ```

11. **[Draft a new release][]** using GitHub web; fill in the fields as follows:

    - From the **release/tag dropdown**: Select the new release tag that you
      just pushed, v0.X.Y.
    - Set the **release title** to the release number (without the "v").
    - Click **Generate release notes** to get the release details inserted into
      the release notes text area.
    - Add the following text atop the generated release notes, but replace the
      `0XY` anchor target with a target appropriate for this release:

      ```markdown
      ## Release summary

      See, https://github.com/google/docsy/blob/main/CHANGELOG.md#0XY
      ```

    - Remove the "New contributors" autogenerated text (if present) since we
      don't publish that as part of our release notes.
    - Select **Create a discussion for this release**.

12. **Publish the release**: click _Publish release_.
13. Test the release with a downstream project, such as [docsy-example].
14. If you find issues, determine whether they need to be fixed immediately. If
    so, get fixes submitted, reviewed and approved. Then publish a dot release:
    go back to step 1.

## Post-release followup

Assuming that Docsy release v0.X.Y has been successfully deployed and use by at
least one downstream project, then perform the following actions before any
further changes are merged into the default branch:

1. Set `version` in [package.json](package.json) to the next planned (or the
   next dot) release with a dev suffix, such as `v0.X.Z-dev.0-unreleased`.
2. (Optional) Run `hugo mod get`.
3. **Submit a PR with your changes**, using a title like "Set NPM package
   version to next unreleased dev".
4. **Get PR approved and merged**.

[contribution guidelines]: https://www.docsy.dev/docs/contribution-guidelines/
[Draft a new release]: https://github.com/google/docsy/releases/new
[docsy-example]: https://github.com/google/docsy-example
[userguide/hugo.yaml]: userguide/hugo.yaml
