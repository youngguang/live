# Create a domain name {#concept_p45_v4j_bfb .concept}

Before creating an ApsaraVideo Live activity, you must add a domain name in the ApsaraVideo Live console.

## Prerequisites { .section}

-   If you want to use ApsaraVideo Live service in China, you must have a domain name that has completed ICP record filing.
-   If the record-filing is pending, you must first apply for ICP record filing.

## Procedure { .section}

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domains** \> **Add Domain**.

    **Note:** You must add an **Ingest Domain** and a **Streaming Domain** respectively.

3.  Configure the**Streaming Domain**, and click **Next**。

    **Note:** 

    -   **Live Center**: refers to the location of the live center. The **Ingest Domain** and the **Streaming Domain** must be in the same region.
    -   **Domain Type**: refers to the acceleration type of the domain name. **Ingest Domain** and **Streaming Domain** correspond to stream ingest acceleration and live streaming acceleration respectively.
    -   **Edge Group**: refers to the area where the domain name can perform acceleration.
    **Streaming Domain** is created successfully.

4.  Click **Back to Domain List**.
5.  Click **Add Domain**.
6.  Configure **Ingest Domain**, and click **Next**.

    **Ingest Domain** is created successfully.

    **Note:** After the domain names are created, you must configure CNAME for the domain names. For more information, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#). After the domain names are successfully configured, the domain names automatically configures acceleration function, and you can use the acceleration function immediately.


