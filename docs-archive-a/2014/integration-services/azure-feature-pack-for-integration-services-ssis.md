---
title: Azure 기능 팩 | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8bca2b4d3ce91f6010fbe01da836efd8a67ca6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728655"
---
# <a name="azure-feature-pack"></a><span data-ttu-id="22588-102">Azure 기능 팩</span><span class="sxs-lookup"><span data-stu-id="22588-102">Azure Feature Pack</span></span>
<span data-ttu-id="22588-103">Azure용 SSIS(SQL Server Integration Services) 기능 팩은 Azure 서비스에 연결하고, Azure 및 온-프레미스 데이터 원본 간에 데이터를 전송하고, Azure에 저장된 데이터를 처리하기 위해 SSIS에 이 페이지에 나열된 구성 요소를 제공하는 확장 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="22588-103">SQL Server Integration Services (SSIS) Feature Pack for Azure is an extension that provides the components listed on this page for SSIS to connect to Azure services, transfer data between Azure and on-premises data sources, and process data stored in Azure.</span></span>

## <a name="components-in-the-feature-pack"></a><span data-ttu-id="22588-104">기능 팩의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="22588-104">Components in the Feature Pack</span></span>
  
-   <span data-ttu-id="22588-105">연결 관리자</span><span class="sxs-lookup"><span data-stu-id="22588-105">Connection Managers</span></span>  
  
    -   [<span data-ttu-id="22588-106">Azure Storage 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="22588-106">Azure Storage Connection Manager</span></span>](connection-manager/azure-storage-connection-manager.md)  
  
    -   [<span data-ttu-id="22588-107">Azure 구독 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="22588-107">Azure Subscription Connection Manager</span></span>](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [<span data-ttu-id="22588-108">Azure Data Lake Store 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="22588-108">Azure Data Lake Store Connection Manager</span></span>](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [<span data-ttu-id="22588-109">Azure Resource Manager 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="22588-109">Azure Resource Manager Connection Manager</span></span>](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [<span data-ttu-id="22588-110">Azure HDInsight 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="22588-110">Azure HDInsight Connection Manager</span></span>](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   <span data-ttu-id="22588-111">작업</span><span class="sxs-lookup"><span data-stu-id="22588-111">Tasks</span></span>  
  
    -   [<span data-ttu-id="22588-112">Azure Blob 업로드 태스크</span><span class="sxs-lookup"><span data-stu-id="22588-112">Azure Blob Upload Task</span></span>](control-flow/azure-blob-upload-task.md)  
  
    -   [<span data-ttu-id="22588-113">Azure Blob 다운로드 작업</span><span class="sxs-lookup"><span data-stu-id="22588-113">Azure Blob Download Task</span></span>](control-flow/azure-blob-download-task.md)  
  
    -   [<span data-ttu-id="22588-114">Azure HDInsight 하이브 태스크</span><span class="sxs-lookup"><span data-stu-id="22588-114">Azure HDInsight Hive Task</span></span>](control-flow/azure-hdinsight-hive-task.md)  
  
    -   <span data-ttu-id="22588-115">[Azure HDInsight Pig 태스크](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="22588-115">[Azure HDInsight Pig Task](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span></span>
  
    -   [<span data-ttu-id="22588-116">Azure HDInsight 클러스터 만들기 태스크</span><span class="sxs-lookup"><span data-stu-id="22588-116">Azure HDInsight Create Cluster Task</span></span>](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [<span data-ttu-id="22588-117">Azure HDInsight 클러스터 삭제 작업</span><span class="sxs-lookup"><span data-stu-id="22588-117">Azure HDInsight Delete Cluster Task</span></span>](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [<span data-ttu-id="22588-118">Azure SQL DW 업로드 태스크</span><span class="sxs-lookup"><span data-stu-id="22588-118">Azure SQL DW Upload Task</span></span>](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [<span data-ttu-id="22588-119">Azure Data Lake Store 파일 시스템 태스크</span><span class="sxs-lookup"><span data-stu-id="22588-119">Azure Data Lake Store File System Task</span></span>](control-flow/file-system-task.md)    
  
-   <span data-ttu-id="22588-120">데이터 흐름 구성 요소</span><span class="sxs-lookup"><span data-stu-id="22588-120">Data Flow Components</span></span>  
  
    -   <span data-ttu-id="22588-121">[Azure Blob 원본](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="22588-121">[Azure Blob Source](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span></span>  
  
    -   [<span data-ttu-id="22588-122">Azure Blob 대상</span><span class="sxs-lookup"><span data-stu-id="22588-122">Azure Blob Destination</span></span>](data-flow/azure-blob-destination.md)  
    
    -   [<span data-ttu-id="22588-123">Azure Data Lake Store 원본</span><span class="sxs-lookup"><span data-stu-id="22588-123">Azure Data Lake Store Source</span></span>](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [<span data-ttu-id="22588-124">Azure Data Lake Store 대상</span><span class="sxs-lookup"><span data-stu-id="22588-124">Azure Data Lake Store Destination</span></span>](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   <span data-ttu-id="22588-125">Azure Blob 열거자 & ADLS File 열거자.</span><span class="sxs-lookup"><span data-stu-id="22588-125">Azure Blob Enumerator & ADLS File Enumerator.</span></span> <span data-ttu-id="22588-126">[Foreach 루프 컨테이너](control-flow/foreach-loop-container.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22588-126">See [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 
## <a name="download-the-feature-pack"></a><span data-ttu-id="22588-127">기능 팩 다운로드</span><span class="sxs-lookup"><span data-stu-id="22588-127">Download the Feature Pack</span></span>  
<span data-ttu-id="22588-128">Azure용 SSIS(SQL Server Integration Services) 기능 팩을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-128">Download the SQL Server Integration Services (SSIS) Feature Pack for Azure.</span></span>  
  
-   [<span data-ttu-id="22588-129">Azure용 Microsoft SQL Server 2014 Integration Services 기능 팩</span><span class="sxs-lookup"><span data-stu-id="22588-129">Microsoft SQL Server 2014 Integration Services Feature Pack for Azure</span></span>](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a><span data-ttu-id="22588-130">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="22588-130">Prerequisites</span></span>  
<span data-ttu-id="22588-131">이 기능 팩을 설치하기 전에 다음과 같은 필수 조건을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-131">You must install the following prerequisites before installing this feature pack.</span></span>  
  
-   <span data-ttu-id="22588-132">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="22588-132">SQL Server Integration Services</span></span>  
-   <span data-ttu-id="22588-133">.Net Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="22588-133">.Net Framework 4.5</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="22588-134">시나리오</span><span class="sxs-lookup"><span data-stu-id="22588-134">Scenarios</span></span>  
  
### <a name="big-data-processing"></a><span data-ttu-id="22588-135">빅 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="22588-135">Big Data Processing</span></span>  
 <span data-ttu-id="22588-136">Azure 커넥터를 사용하여 다음과 같은 빅 데이터 처리 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-136">Use Azure Connector to complete following big data processing work:</span></span>  
  
1.  <span data-ttu-id="22588-137">Azure Blob 업로드 태스크를 사용하여 Azure Blob Storage에 입력 데이터를 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-137">Use the Azure Blob Upload Task to upload input data to Azure Blob Storage.</span></span>  
  
2.  <span data-ttu-id="22588-138">Azure HDInsight 클러스터 만들기 태스크를 사용하여 Azure HDInsight 클러스터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22588-138">Use the Azure HDInsight Create Cluster Task to create an Azure HDInsight cluster.</span></span> <span data-ttu-id="22588-139">자체 클러스터를 사용하려는 경우 이 단계는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="22588-139">This step is optional if you want to use your own cluster.</span></span>  
  
3.  <span data-ttu-id="22588-140">Azure HDInsight Hive 태스크 또는 Azure HDInsight Pig 태스크를 사용하여 Azure HDInsight 클러스터에서 Pig 또는 Hive 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-140">Use the Azure HDInsight Hive Task or Azure HDInsight Pig Task to invoke a Pig or Hive job on the Azure HDInsight cluster.</span></span>  
  
4.  <span data-ttu-id="22588-141">2단계에서 주문형 HDInsight 클러스터를 만든 경우 Azure HDInsight 클러스터 삭제 태스크를 사용하여 사용한 HDInsight 클러스터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-141">Use the Azure HDInsight Delete Cluster Task to delete the HDInsight Cluster after use if you have created an on-demand HDInsight cluster in step #2.</span></span>  
  
5.  <span data-ttu-id="22588-142">Azure HDInsight Blob 다운로드 태스크를 사용하여 Azure Blob Storage에서 Pig/Hive 출력 데이터를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-142">Use the Azure HDInsight Blob Download Task to download the Pig/Hive output data from the Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="22588-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span><span class="sxs-lookup"><span data-stu-id="22588-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span></span>  
  
### <a name="cloud-data-archiving"></a><span data-ttu-id="22588-144">클라우드 데이터 보관</span><span class="sxs-lookup"><span data-stu-id="22588-144">Cloud Data Archiving</span></span>  
 <span data-ttu-id="22588-145">SSIS 패키지의 Azure Blob 대상을 사용하여 Azure Blob Storage에 출력 데이터를 쓰거나 Azure Blob 원본을 사용하여 Azure Blob Storage에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="22588-145">Use the Azure Blob Destination in an SSIS package to write output data to an Azure Blob Storage, or use the Azure Blob Source to read data from an Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="22588-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span><span class="sxs-lookup"><span data-stu-id="22588-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span></span>  
  
 <span data-ttu-id="22588-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span><span class="sxs-lookup"><span data-stu-id="22588-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span></span>  
  
 <span data-ttu-id="22588-148">또한 Azure Blob 열거자에서 Foreach 루프 컨테이너를 사용하여 다중 blob 파일의 데이터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="22588-148">And use the Foreach Loop Container with Azure Blob Enumerator to process data in multiple bob files.</span></span>  
  
 <span data-ttu-id="22588-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span><span class="sxs-lookup"><span data-stu-id="22588-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span></span>  
  
  
