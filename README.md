# QCR Workflow Templates
This repository contains template workflows for GitHub that automate processes such as Debianising ROS packages. For instructions on how to add a new workflow template to this repository please see the documentation provided [here](https://docs.github.com/en/actions/learn-github-actions/sharing-workflows-with-your-organization).

## Using QCR Workflows

### Public Repositories

To use a QCR workflow in a public QCR managed repository:

1. navigate to the main page of the repository on GitHub

2. Select Actions from the top menu as shown in the image below

![Selecting Actions](https://docs.github.com/assets/images/help/repository/actions-tab.png)

3. Select the QCR workflow that is relevent to your project

![Selecting Workflow](/media/qcr-workflow.png)

4. Make any required changes to the workflow (e.g., os versions, python versions or branch names), then press *Start Commit*.

![Selecting Workflow](/media/update.png)

### Private Repositories

To use a QCR workflow in a private QCR managed repository:

1. navigate to the main page of the repository on GitHub

2. Select Actions from the top menu as shown in the image below

![Selecting Actions](https://docs.github.com/assets/images/help/repository/actions-tab.png)

3. Select *set up a workflow yourself*

![DIY Workflow](/media/diy.png)

4. Delete the automatically generated content, and replace it with content of the workflow found in ``/workflow-templates`` similar to step 4 in the public repository instructions.

## Available Workflows

The following workflows are currently available.

### Build Debian Release

This workflow allows you to build Debian releases from catkinised packages (i.e., packages containing a package.xml and CMakeLists.txt file that imports the catkin toolset). The generated debians are then automatically added to the QCR public repositories. This allows your code to be installed via the apt package manager, which will also automatically install any packages that your package depends on.

To use this package, simply add it to your repository using the steps described above, then from the main page of your repository, generate a new Release. This will cause the workflow to automatically build a debian based on the released commit.

Please note that the files that will be included in the debian are determined by the install instructions in your CMakeLists.txt file. As such, it is worth testing the installation process locally using ``catkin_make install`` before you attempt to build a debian using this workflow to make sure that all required files are installed correctly.

**Important**: This workflow will only work on repositories owned by the QCR organisation. The QCR public repository will reject any packages generated from other sources.

