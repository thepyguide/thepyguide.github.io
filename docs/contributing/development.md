# Working with project code
This section outlines the basic guidelines and conventions for the
source code of this guide.

## Directory structure
The `docs/` folder consists of the source code for the guide.

- `docs/_images/` stores the images that are used in the guide.
- `docs/_styles/` stores the CSS stylesheets used for website.
- `docs/_templates/` stores Jinja templates used for websites.
- Other directories and files in this folder correspond to the appropriate
  sections in the guide.

## Theme
This guide uses [MkDocs Material theme](https://squidfunk.github.io/mkdocs-material/) theme.

Elements of the theme that are commonly used are listed below with
their corresponding documentation. For other elements, please see
the documentation of Material theme.

- [Admonitions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/)
- [Annotations](https://squidfunk.github.io/mkdocs-material/reference/annotations/)
- [Code Blocks](https://squidfunk.github.io/mkdocs-material/reference/code-blocks/)
- [Content Tabs](https://squidfunk.github.io/mkdocs-material/reference/content-tabs/)

## Code blocks
Code blocks in the guide are showcased using the [Content Tabs](https://squidfunk.github.io/mkdocs-material/reference/content-tabs/) feature of
the theme.

Each code block has at least two tabs: one for code, other for output

Example:
```md
=== "Code"

    ```py
    print('code here!')
    ```

=== "Output"

    <!-- Expected output is added here as a markdown codeblock -->

    ```
    code here!
    ```
```
Above code is displayed as:

=== "Code"

    ```py
    print('code here!')
    ```

=== "Output"

    <!-- Expected output is added here as a markdown codeblock -->

    ```
    code here!
    ```

In some cases, `Output` tab is named as `Error` tab indicating that
an error is raised by the code.

Sometimes there may be multiple `Output` tabs to showcase different
outputs (e.g. for different inputs). In this case, each output 
tab is numbered.

```md
=== "Code"

    ```py
    num = input('enter a number:')
    ```

=== "Output #1"

    ```
    enter a number: 25
    ```

=== "Output #2"

    ```
    enter a number: 22
    ```
```
