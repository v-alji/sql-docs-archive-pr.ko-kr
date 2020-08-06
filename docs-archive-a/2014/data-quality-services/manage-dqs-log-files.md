---
title: DQS 로그 파일 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ca85772b8cc8aca41b75ad05d028bc444f280378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660149"
---
# <a name="manage-dqs-log-files"></a><span data-ttu-id="12eb6-102">DQS 로그 파일 관리</span><span class="sxs-lookup"><span data-stu-id="12eb6-102">Manage DQS Log Files</span></span>
  <span data-ttu-id="12eb6-103">DQS([!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] ) 로그 파일은 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]및 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]관련 문제를 진단하고 해결하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) log files help you in diagnosing and troubleshooting issue with [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="12eb6-104">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]및 [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]에 대해 로그 파일이 개별적으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-104">Separate log files are generated for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
 <span data-ttu-id="12eb6-105">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 를 사용하여 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 기능 및 모듈의 로그 심각도 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-105">You can use [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] to configure the log severity setting for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] features and modules.</span></span> <span data-ttu-id="12eb6-106">또한 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 컴퓨터에서 DQS_MAIN 데이터베이스 및 XML 파일의 DQS 로그 구성 설정을 수동으로 변경하여 DQS 로그 파일의 다른 (고급) 설정을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-106">Additionally, you can also configure some other (advanced) settings for the DQS log files by manually changing the DQS log configuration settings in the DQS_MAIN database and an XML file on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer.</span></span>  
  
##  <a name="data-quality-server-log-file"></a><a name="DQSServer"></a><span data-ttu-id="12eb6-107">Data Quality 서버 로그 파일</span><span class="sxs-lookup"><span data-stu-id="12eb6-107">Data Quality Server Log File</span></span>  
 <span data-ttu-id="12eb6-108">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로그 파일 DQServerLog.DQS_MAIN.log에는 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]에서 실행된 작업에 대한 로그가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-108">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, DQServerLog.DQS_MAIN.log, includes logs of activities that are run on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="12eb6-109">SQL Server의 기본 인스턴스를 설치한 경우 DQServerLog.DQS_MAIN.log 파일은 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-109">If you installed the default instance of SQL Server, the DQServerLog.DQS_MAIN.log file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log.</span></span> <span data-ttu-id="12eb6-110">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로그 파일에는 다음과 같은 정보 조각이 각각 파이프(|)로 구분되어 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-110">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file contains the following pieces of information, each delimited by a pipe (|):</span></span>  
  
-   <span data-ttu-id="12eb6-111">날짜 및 시간</span><span class="sxs-lookup"><span data-stu-id="12eb6-111">Date and time</span></span>  
  
-   <span data-ttu-id="12eb6-112">스레드 이름</span><span class="sxs-lookup"><span data-stu-id="12eb6-112">Thread name</span></span>  
  
-   <span data-ttu-id="12eb6-113">스레드 ID</span><span class="sxs-lookup"><span data-stu-id="12eb6-113">Thread ID</span></span>  
  
-   <span data-ttu-id="12eb6-114">로그 심각도(치명적, 오류, 경고, 정보 및 디버그)</span><span class="sxs-lookup"><span data-stu-id="12eb6-114">Log severity (FATAL, ERROR, WARN, INFO, and DEBUG)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12eb6-115">디버그 로그 심각도는 자세히와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-115">The DEBUG logging severity is same as Verbose.</span></span>  
  
-   <span data-ttu-id="12eb6-116">UID(내부 DQS 인프라 ID)</span><span class="sxs-lookup"><span data-stu-id="12eb6-116">UID (internal DQS infrastructure ID)</span></span>  
  
-   <span data-ttu-id="12eb6-117">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="12eb6-117">Namespace</span></span>  
  
-   <span data-ttu-id="12eb6-118">클래스 및 메서드</span><span class="sxs-lookup"><span data-stu-id="12eb6-118">Class and method</span></span>  
  
-   <span data-ttu-id="12eb6-119">메시지</span><span class="sxs-lookup"><span data-stu-id="12eb6-119">Message</span></span>  
  
 <span data-ttu-id="12eb6-120">또한 로그 파일은 애플리케이션 버전, 컴퓨터 이름, 사용자 이름 및 운영 체제에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-120">Along with these, the log file also displays information about the application version, computer name, user name, and operating system.</span></span>  
  
 <span data-ttu-id="12eb6-121">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로그 파일의 예제 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-121">A sample entry in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file looks like the following:</span></span>  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 <span data-ttu-id="12eb6-122">DQServerLog.DQS_MAIN.log 파일은 롤링 파일이며 기존 로그 파일이 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로그 구성 설정에 지정된 롤링 파일 크기 제한을 초과하면 새 로그 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-122">The DQServerLog.DQS_MAIN.log file is a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="12eb6-123">자세한 내용은 [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12eb6-123">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="data-quality-client-log-file"></a><a name="DQSClient"></a><span data-ttu-id="12eb6-124">로그 파일 Data Quality Client</span><span class="sxs-lookup"><span data-stu-id="12eb6-124">Data Quality Client Log File</span></span>  
 <span data-ttu-id="12eb6-125">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로그 파일 DQClientLog.log에는 클라이언트 쪽 로그가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-125">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file, DQClientLog.log, includes the client side logs.</span></span> <span data-ttu-id="12eb6-126">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로그 파일은 %APPDATA%\SSDQS\Log에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-126">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="12eb6-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로그 파일에는 서버 로그 파일과 유사하지만 클라이언트 쪽에 대한 정보 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file contains similar set of information as in the server log file, but for the client side.</span></span>  
  
 <span data-ttu-id="12eb6-128">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로그 파일과 마찬가지로 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로그 파일도 롤링 파일이며 기존 로그 파일이 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 로그 구성 설정에 지정된 롤링 파일 크기 제한을 초과하면 새 로그 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-128">As with the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is also a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log configuration settings.</span></span> <span data-ttu-id="12eb6-129">자세한 내용은 [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12eb6-129">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="dqs-cleansing-component-log-file"></a><a name="DQSCleansing"></a><span data-ttu-id="12eb6-130">DQS 정리 구성 요소 로그 파일</span><span class="sxs-lookup"><span data-stu-id="12eb6-130">DQS Cleansing Component Log File</span></span>  
 <span data-ttu-id="12eb6-131">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 로그 파일 DQSSSISLog.log에는 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]를 사용하여 수행된 작업에 대한 로그가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-131">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file, DQSSSISLog.log, includes logs of activities performed using the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="12eb6-132">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 구성 요소 로그 파일은 %APPDATA%\SSDQS\Log에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-132">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] component log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="12eb6-133">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 로그 파일에는 서버 로그 파일과 유사하지만 [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]에 대한 정보 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-133">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file contains similar set of information as in the server log file, but for the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
##  <a name="related-tasks"></a><a name="RT"></a> <span data-ttu-id="12eb6-134">관련 작업</span><span class="sxs-lookup"><span data-stu-id="12eb6-134">Related Tasks</span></span>  
  
|<span data-ttu-id="12eb6-135">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="12eb6-135">Task Description</span></span>|<span data-ttu-id="12eb6-136">항목</span><span class="sxs-lookup"><span data-stu-id="12eb6-136">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="12eb6-137">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]를 사용하여 DQS 로그 파일의 로그 심각도 설정을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-137">Describes how to configure log severity settings for DQS log files using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="12eb6-138">DQS 로그 파일에 대한 심각도 수준 구성</span><span class="sxs-lookup"><span data-stu-id="12eb6-138">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|<span data-ttu-id="12eb6-139">DQS 로그 파일의 고급 설정을 수동으로 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12eb6-139">Describes how to manually configure advanced settings for DQS log files.</span></span>|[<span data-ttu-id="12eb6-140">Configure Advanced Settings for DQS Log Files</span><span class="sxs-lookup"><span data-stu-id="12eb6-140">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a><span data-ttu-id="12eb6-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12eb6-141">See Also</span></span>  
 [<span data-ttu-id="12eb6-142">dqs 관리</span><span class="sxs-lookup"><span data-stu-id="12eb6-142">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  
