
# Maintaining the TDM23 MkDocs Project

This document outlines the process for maintaining and updating the TDM23 MkDocs project. It covers the setup of the development environment, the build process, and deployment.

## Project Structure

The project has the following key directories and files:

- `.venv/`: Localized python packages for deploying users guide if using virtual environment *(ignored by git)*.
- `docs/`: Serves as the source directory for the documentation, containing all Markdown and related files.
  - `css/`: Holds customized styles used for tables and pages.
  - `images/`: Stores images used in the documentation.
  - `pages/`: Contains individual Markdown files for different sections of the documentation.
    - `_assets/`: Houses the assets used in pages. _assets/ folder needs to be housed here to be accessed publicly. Folder includes additional HTML assets used in the documentation.
      - `gisdk_assets`: Stores HTML assets specifically for GISDK Macros in TDM23.
  - `index.md`: Represents the starting page of the documentation.
- `site/`: Automatically populated from docs/ files, ready for deployment to GitHub Pages. *Note: This is ignored by git as site deployment is handled in a versioned environment branch `gh-pages` through **mike**.*

## Development Environment Setup

To get started with maintaining the documentation, you need to set up the development environment:

1. **Start an Environment**

    1.1. **Initialize the Conda Environment**:

    - Navigate to the project root directory.
    - Create an Anaconda environment if one does not already exist:
      ```
      conda create --name tdm23_mkdocs
      ```
    - Activate the Conda environment:
      ```
      conda activate tdm23_mkdocs
      ```
    - Install PIP in Conda environment:
      ```
      conda install pip
      ```
    <!-- - To deactivate the Conda environment, run:
      ```
      conda deactivate
      ``` -->

    1.2. **Using Virtual Environment (`venv`) Alternative**:

    - Navigate to the project root directory.
    - Create a virtual environment if one does not already exist:
      ```
      python -m venv .venv
      ```
    - Activate the virtual environment:
      - Windows:
        ```
        .\.venv\Scripts\activate
        ```
      - macOS/Linux:
        ```
        source .venv/bin/activate
        ```
    <!-- - To deactivate the virtual environment, run:
      ```
      deactivate
      ``` -->

2. **Install Dependencies**:

   - In the active environment, install the required dependencies using the `requirements.txt` file:
     ```
     pip install -r requirements.txt
     ```

## Regular Maintenance

- Update the content in the `docs/` directory as needed.
    - For *TDM23 Macros*, run `docs\gisdkdoc\build.bat` in `tdm23`, copy the files generated in `docs\build` from `tdm23` to `docs\pages\_assets\gisdk_assets` of this repo.
    - For *Utility Platform*, 
        - in `tdm23_sr`, set `MODE = "usersguide"` in `ui_portal\html_generator\html_generator.py`, then run `python .\portal.py`
        - copy the files generated in `ui_portal\html_generator\static_documentations` from `tdm23_sr` to `docs\pages\_assets\utility_platform\static\static_documentations` of this repo
        - copy and rename `ui_portal\html_generator\list.html` to `docs\pages\_assets\utility_platform\utility_platform_embed.html`
        - change absolute reflinks to documentations to relative ones - `".\static\static_documentations...` and `'.\static\static_documentations...`

- Maintain the structure of pages in `mkdocs.yml` as needed.
- Maintain quoted contents:
    - *Known Issues and Solutions*
    - *Data Dictionary*
- Regularly check for updates to MkDocs and the Material theme, and update `requirements.txt` accordingly.
- After any update or change, remember to rebuild the site and test it locally before deployment.

## Local Testing

A local server more accurately reflects the behavior of the documentation site on the web in contrast to opening the html file locally. Before deploying, you can test the site locally:

- Start a local server to see the latest site using 
  ```
  mkdocs serve
  ```
  or, to see multiple versions, using 
  ```
  mike serve
  ```
  For a quick launch in Conda Environment, you can run `local_test_with_mkdocs.bat`. 
- View the site at `http://127.0.0.1:8000/` or `http://localhost:8000/` to ensure all changes appear as expected.

## Deployment

- Once you're satisfied with the changes, deploy the site to the appropriate version:
  - The **-p** flag is used to push the changes to the `gh-pages` branch
    ```
    mike deploy 0.0 -p
    ```
- The GitHub page is set up to automatically deploy the version indicated in the set-default command
  ```
  mike set-default 0.0 -p
  ```

## Updating Dependencies

- To update dependencies and freeze the current state of packages:

  ```
  pip install mkdocs-material
  pip freeze > requirements.txt
  ```

## Additional Commands

**mkdocs**

- Create a new project

  ```
  mkdocs new [dir-name]
  ```
- Print a help message:

  ```
  mkdocs -h
  ```
- Run documentation locally (without consideration of versions)
  ```
  mkdocs serve
  ```

**mike**

- Deploy a specific version and push to the remote repository

  ```
  mike deploy 0.0 -p
  ```
- Set a specific version as the default on the site and push the change

  ```
  mike set-default 0.0 -p
  ```
- Serve the documentation locally for testing

  ```
  mike serve
  ```
- Delete a specific version or alias of the documentation

  ```
  mike delete [version/alias]
  ```
- List all deployed versions and aliases

  ```
  mike list
  ```
- Change the title of a specific version

  ```
  mike retitle [version] [new title]
  ```
- Add a new alias to an existing version

  ```
  mike alias [version] [new alias]
  ```
- Manage properties for each version of the documentation

  ```
  mike props [version] [property]
  ```
