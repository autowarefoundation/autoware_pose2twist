# autoware_pose2twist

This ROS 2 package calculates a velocity from the history of an input pose. It publishes the result as a twist, and also publishes its linear-x and angular-z values for debugging. See the [package documentation](autoware_pose2twist/README.md) for its topics.

The package comes from [Autoware Universe at `8885c4f2420c64f6d6a9569ab531eeae7e119660`](https://github.com/autowarefoundation/autoware_universe/tree/8885c4f2420c64f6d6a9569ab531eeae7e119660/localization/autoware_pose2twist). The source license, notices, maintainers, and changelog remain with the package.

## Installation

If your workspace already contains this package in Autoware Universe, use a Universe revision that removes it before you import this repository. Stable Autoware releases that still contain the package cannot use both copies in one workspace.

After the package appears in the Autoware Index, run these commands from your Autoware workspace root:

```sh
aw-index-cli compose --rosdistro jazzy --packages autoware_pose2twist
vcs import src < repositories/autoware-index.repos
rosdep install --from-paths src --ignore-src --rosdistro jazzy -y
colcon build --symlink-install --packages-up-to autoware_pose2twist
source install/setup.bash
```

## CI

The `autoware-index-validate` workflow builds the package, runs its unit and ament lint tests, and runs clang-tidy against the latest published Autoware Core image for Jazzy. It runs on pull requests, pushes to `main`, and manual requests. Core dependencies come from the image.

The daily `sync-files` workflow maintains the shared files listed in [`.github/sync-files.yaml`](.github/sync-files.yaml) from the Foundation templates. The package-specific Index validation workflow remains local to this repository.

Sync Files requires the Foundation GitHub App to have repository access, the `APP_ID` and `PRIVATE_KEY` secrets, and repository auto-merge enabled. Public pull requests use pre-commit.ci for formatting checks. Run `pre-commit run --all-files` before you open a pull request.
