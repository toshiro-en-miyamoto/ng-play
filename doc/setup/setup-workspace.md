# Setup Angular Workspaces

Ref: https://angular.io/guide/file-structure

You develop applications in the context of an Angular workspace. A **workspace** contains the files for one or more projects. A **project** is the set of files that comprise a standalone application or a shareable library.

The Angular CLI ng new command creates a workspace, but **don't do this**.

```
$ ng new my-project
```

When you run this command, the CLI installs the necessary Angular npm packages and other dependencies in a new workspace, with a root-level application named `my-project`.

This default behavior is suitable for a typical **multi-repo** development style where each application resides in its own workspace. Beginners and intermediate users are encouraged to use ng new to create a separate workspace for each application.

Angular also supports workspaces with multiple projects. This type of development environment is suitable for advanced users who are developing shareable libraries, and for enterprises that use a **monorepo** development style, with a single repository and global configuration for all Angular projects.

To set up a monorepo workspace, you should skip the creating the root application.


## Setting up for a Multi-Project Workspace

If you intend to have multiple projects in a workspace, you can skip the initial application generation when you create the workspace, and give the workspace a unique name. The following command creates a workspace with all of the workspace-wide configuration files, but no root-level application.

```
$ ng new my-workspace --createApplication="false"  --routing="true" --style="scss"
```

The preceeding command creates the following workspace structure:

```
my-workspace/
  angular.json
  ...             (other workspace-wide config files)
```

`angular.json` doesn't have any application:

```
{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "version": 1,
  "newProjectRoot": "projects",
  "projects": {}
}
```

## Generating a Project in the Workspace

Once a workspace is created, you will generate new project in the workspace:

```
$ cd my-workspace
$ ng generate application my-first-app
```

The preceeding command creates the following workstapce structure:

```
my-workspace/
  ...             (workspace-wide config files)
  projects/       (generated applications and libraries)
    my-first-app/ --(an explicitly generated application)
      ...         --(application-specific config)
      e2e/        ----(corresponding e2e tests)
         src/     ----(e2e tests source)
         ...      ----(e2e-specific config)
      src/        --(source and support files for application)
```

Now that a project is generated, `angular.json` has the project:

```
{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "version": 1,
  "newProjectRoot": "projects",
  "projects": {
    "my-first-app": {
      "projectType": "application",
      "schematics": {},
      "root": "projects/my-first-app",
      "sourceRoot": "projects/my-first-app/src",
      "prefix": "app",
      ...
      ...
    }},
  "defaultProject": "my-first-app"
}
```

As the new project is specified as the default one, `ng serve` will successfully serve the application.
