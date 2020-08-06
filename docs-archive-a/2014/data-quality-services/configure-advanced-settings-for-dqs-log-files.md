---
title: DQS 로그 파일에 대한 고급 설정 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- log files,advanced settings
- dqs log files,advanced settings
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad41b0cac95f9bfe5565ccbac16b0fda3e28ddf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728736"
---
# <a name="configure-advanced-settings-for-dqs-log-files"></a><span data-ttu-id="356e9-102">Configure Advanced Settings for DQS Log Files</span><span class="sxs-lookup"><span data-stu-id="356e9-102">Configure Advanced Settings for DQS Log Files</span></span>
  <span data-ttu-id="356e9-103">이 항목에서는 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 및 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로그 파일에 대해 로그 파일의 롤링 파일 크기 제한을 설정하거나, 이벤트의 타임스탬프 패턴을 설정하는 등 고급 설정을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-103">This topic describes how to configure advanced settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log files, such as set the rolling file size limit of the log files, set the time stamp pattern of the events, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="356e9-104">이러한 작업은 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]를 사용하여 수행할 수 없으며 고급 사용자 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-104">These activities cannot be performed using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and is intended for advanced users only.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="356e9-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="356e9-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="356e9-106">보안</span><span class="sxs-lookup"><span data-stu-id="356e9-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="356e9-107">권한</span><span class="sxs-lookup"><span data-stu-id="356e9-107">Permissions</span></span>  
  
-   <span data-ttu-id="356e9-108">DQS_MAIN 데이터베이스에서 A_CONFIGURATION 테이블의 구성 설정을 수정하려면 Windows 사용자 계정이 SQL Server 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-108">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to modify configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
-   <span data-ttu-id="356e9-109">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로깅 설정을 구성하려면 DQLog.Client.xml 파일을 수정할 컴퓨터에서 Administrators 그룹의 멤버로 로그온해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-109">You must be logged on as a member of the Administrators group on the computer where you are modifying the DQLog.Client.xml file to configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] logging settings.</span></span>  
  
##  <a name="configure-data-quality-server-log-settings"></a><a name="DQSServer"></a><span data-ttu-id="356e9-110">Data Quality 서버 로그 설정 구성</span><span class="sxs-lookup"><span data-stu-id="356e9-110">Configure Data Quality Server Log Settings</span></span>  
 <span data-ttu-id="356e9-111">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로그 설정은 DQS_MAIN 데이터베이스의 A_CONFIGURATION 테이블에서 **ServerLogging** 행의 **VALUE** 열에 XML 형식으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-111">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings are present in an XML format in the **VALUE** column of the **ServerLogging** row in the A_CONFIGURATION table in the DQS_MAIN database.</span></span> <span data-ttu-id="356e9-112">다음 SQL 쿼리를 실행하여 구성 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-112">You can run the following SQL query to view the configuration information:</span></span>  
  
```sql  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'; 
```  
  
 <span data-ttu-id="356e9-113">로깅의 구성 설정을 변경하려면 **ServerLogging** 행의 **VALUE**[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 열에서 알맞은 정보를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-113">You must update the appropriate information in the **VALUE** column of the **ServerLogging** row to change the configuration settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging.</span></span> <span data-ttu-id="356e9-114">이 예에서는 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로그 설정을 업데이트하여 롤링 파일 크기 제한을 25000KB로 설정합니다(기본값은 20000KB).</span><span class="sxs-lookup"><span data-stu-id="356e9-114">In this example, we will update the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings to set the rolling file size limit to 25000 KB (the default is 20000 KB).</span></span>  
  
1.  <span data-ttu-id="356e9-115">Microsoft SQL Server Management Studio를 시작하고 적합한 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-115">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="356e9-116">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-116">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="356e9-117">쿼리 편집기 창에서 다음 SQL 문을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-117">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  <span data-ttu-id="356e9-118">F5 키를 눌러 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-118">Press F5 to execute the statements.</span></span> <span data-ttu-id="356e9-119">**결과** 창에서 문이 성공적으로 실행되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-119">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
5.  <span data-ttu-id="356e9-120">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로깅 구성 변경 내용을 적용하려면 다음 Transact-SQL 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-120">To apply changes done to the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging configuration, you must run the following Transact-SQL statements.</span></span> <span data-ttu-id="356e9-121">새 쿼리 편집기 창을 열고 다음 Transact-SQL 문을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-121">Open a new Query Editor window, and paste the following Transact-SQL statements:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
    ```  
  
6.  <span data-ttu-id="356e9-122">F5 키를 눌러 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-122">Press F5 to execute the statements.</span></span> <span data-ttu-id="356e9-123">**결과** 창에서 문이 성공적으로 실행되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-123">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="356e9-124">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로깅 설정 구성이 동적으로 생성되어 DQS_MAIN.Log 파일에 저장됩니다. SQL Server의 기본 인스턴스를 설치한 경우 이 파일은 대개 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-124">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging settings configuration is dynamically generated and stored in the DQS_MAIN.Log file, which is typically available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log if you installed the default instance of SQL Server.</span></span> <span data-ttu-id="356e9-125">그러나 이 파일에서 직접 변경한 내용은 유지되지 않고 DQS_MAIN 데이터베이스의 A_CONFIGURATION 테이블에 있는 구성 설정이 이 변경 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-125">However, changes done directly in this file do not hold, and are overwritten by the configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
##  <a name="configure-data-quality-client-log-settings"></a><a name="DQSClient"></a><span data-ttu-id="356e9-126">Data Quality Client 로그 설정 구성</span><span class="sxs-lookup"><span data-stu-id="356e9-126">Configure Data Quality Client Log Settings</span></span>  
 <span data-ttu-id="356e9-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]로그 설정 구성 파일 DQLog.Client.xml은 일반적으로 C:\Program FILES\MICROSOFT SQL server\120\tools\binn\dq\config에서 사용할 수 있습니다. XML 파일의 내용은 로그 구성 설정에 대해 이전에 수정한 XML 파일과 비슷합니다 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="356e9-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log setting configuration file, DQLog.Client.xml, is typically available at C:\Program Files\Microsoft SQL Server\120\Tools\Binn\DQ\config. The contents of the XML file is similar to the XML file that you modified earlier for the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="356e9-128">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로그 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="356e9-128">To configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log settings:</span></span>  
  
1.  <span data-ttu-id="356e9-129">XML 편집 도구나 메모장을 관리자로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-129">Run any XML editing tool or notepad as an administrator.</span></span>  
  
2.  <span data-ttu-id="356e9-130">DQLog.Client.xml 파일을 도구나 메모장에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-130">Open the DQLog.Client.xml file in the tool or notepad.</span></span>  
  
3.  <span data-ttu-id="356e9-131">필요한 사항을 변경하고 파일을 저장하여 새 로깅 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="356e9-131">Make the required changes, and save the file to apply the new logging changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356e9-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="356e9-132">See Also</span></span>  
 [<span data-ttu-id="356e9-133">DQS 로그 파일에 대한 심각도 수준 구성</span><span class="sxs-lookup"><span data-stu-id="356e9-133">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  
