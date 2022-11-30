# SnapLogic Integration

Integrate SnapLogic with the  and deploy bots. Authenticate yourself to access a  and deploy or perform other operations by using various  APIs.

SnapLogic is a data integration platform that can connect to any source, and deliver data in the most suitable format for analytical solutions. SnapLogic has many pre-built connectors called snaps. Snaps are the building blocks of a pipeline that perform a single function such as reading, writing, or acting on data. A pipeline is a collection of snaps that orchestrate data flow between endpoints. You can use these snaps to integrate data from applications to derive insights. You can easily integrate  to variety of applications using the SnapLogic Intelligent Integration Platform \(IIP\). The SnapLogic is an industry leading iPaaS \(Integration Platform as a service\) vendor with single platform to integrate applications, data, and things seamlessly.

![SnapLogic and A360 Integratoin](image/Snaplogic-A360-Integration.png)

# Calling  bots from SnapLogic

In order to deploy a bot, you first authenticate and get a valid token. With a valid token you will be able to deploy a bot in  from SnapLogic.

Make sure you have a valid SnapLogic account. If you do not already have an SnapLogic account, you can register for a [30-day free trial](https://www.snaplogic.com/free-trial-agilisium).

Perform the following steps to deploy a bot from the SnapLogic:

1.  Log in to your SnapLogic account with the provided credentials, and then choose the **Manager** section.

2.  You can create or modify an existing Pipeline. You will derive the inputs from the Pipeline to feed your  bot that you are planning to deploy. For more information on Working with Pipelines, see [Working with Pipelines](https://docs-snaplogic.atlassian.net/wiki/spaces/SD/pages/1439001/Working+with+Pipelines).

3.  Search for the Rest snap, and Mapper and attach them as shown in the image, you can drag and attach the snaps together in the canvas.
Download the [sample snaps](sample/NM-pipeline-0_2022_11_15.slp) and update it with your Control Room URL, credentils, and other required parameters. You can use it while building your pipeline.

4.  Double-click on the **REST Post** snap and enter the details to get authenticated to access the  Control Room:

    * Enter a Label in the **Label** field.

    *  Enter the Control Room URL along with the authentication API in the **Service URL** field.

    *  Enter the body with the username and password in the **HTTP Entity field**.

5.  Double-click on the Mapper snap and enter the details to capture the token from the authentication. Use the mapping table to extract the token and map it to a variable. For example: `$response.entity.token` is mapped to `$token`.

    ![SnapLogic Integration](image/SnapLogic-description.png)

6.  Double-click on the REST post snap and enter the details to deploy a bot:

    *  Enter a Label in the **Label** field.

    *   Enter the Control Room URL in the **Service URL** field.

    *   Enter the body with the username and password in the **HTTP Entity field**.

    *   Pass the token saved in the Mapper snap to the **HTTP header**.