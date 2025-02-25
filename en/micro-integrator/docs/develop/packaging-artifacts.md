# Packaging Synapse artifacts

To package Synapse artifacts, you need to create a [Composite Application Project](../../../develop/creating-projects/#composite-application-project).
Use one of the following methods:

## Using an existing composite application

If you have an already created composite appliction project, do the following to package the [Synapse artifacts](creating-artifacts/creating-an-api.md) into the composite application:

1.  Select the `pom.xml` file that is under the composite application project in the project explorer.  
    ![Create CAPP](../../assets/img/create_project/capp_proj_explorer.png)
2.  In the **Dependencies** section, select the artifacts from each of
    the projects.

    > **Note:** If you have created a custom mediator artifact, it should be packaged in the same composite application along with the other artifacts that uses the mediator.
    
    ![Create CAPP](../../assets/img/create_project/capp_dependencies.png)

3.  Save the artifacts.

## Creating a new composite application

If you have not previously created a composite application project, do the following to package the artifacts in your ESB Config project.

1.  Open the **Getting Started** view and click **Miscellaneous → Create
    New Composite Application** .  
    ![Create new CAPP](../../assets/img/create_project/create_new_capp.png) 
2.  In the **New Composite Application Project** dialog that opens, s
    elect the artifacts from the relevant ESB projects and click
    **Finish** .  
    ![Create new CAPP](../../assets/img/create_project/create_new_capp_dialog.png)

Alternatively,

1.  Right-click the project explorer and click **New -> Project** .  
    ![Create new CAPP](../../assets/img/create_project/create_new_project_capp.png)
2.  In the **New Project** dialog that opens, select **Composite
    Application Project** from the list and click **Next** .  
    ![Create new CAPP](../../assets/img/create_project/create_new_project_capp_dialog.png)
3.  Give a name for the **Composite Application** project and select the
    artifacts that you want to package.  
    ![Create new CAPP](../../assets/img/create_project/create_new_project_capp_select_dependencies.png)
4.  In the **Composite Application Project POM Editor** that opens,
    under **Dependencies** , note the information for each of the
    projects you selected earlier.  
    ![Create new CAPP](../../assets/img/create_project/create_new_project_capp_dependencies_view.png)
