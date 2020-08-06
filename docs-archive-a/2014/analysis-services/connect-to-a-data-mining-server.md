---
title: 데이터 마이닝 서버에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
- getting started
ms.assetid: 85962ad6-d840-4bc6-905e-c667c3276944
author: minewiskan
ms.author: owend
ms.openlocfilehash: 528dee62e9074b0d9df6668182c04282500639e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648029"
---
# <a name="connect-to-a-data-mining-server"></a><span data-ttu-id="b72e6-102">데이터 마이닝 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="b72e6-102">Connect to a Data Mining Server</span></span>
  <span data-ttu-id="b72e6-103">![연결 단추](media/misc-connection.gif "연결 단추")</span><span class="sxs-lookup"><span data-stu-id="b72e6-103">![Connections button](media/misc-connection.gif "Connections button")</span></span>  
  
 <span data-ttu-id="b72e6-104">**연결** 단추를 클릭 하 여 기존 연결을 선택 하거나 인스턴스에 대 한 새 연결을 만듭니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b72e6-104">Click the **Connection** button to select an existing connection, or to create a new connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b72e6-105">**서버에 연결해야 하는 이유는 무엇입니까?**</span><span class="sxs-lookup"><span data-stu-id="b72e6-105">**Why do I need to connect to a server?**</span></span>  
  
 <span data-ttu-id="b72e6-106">연결을 만들면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에서 제공하는 데이터 마이닝 알고리즘을 사용하여 서버에 최적화된 처리 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-106">When you create a connection, it enables you to use the data mining algorithms that are provided by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and to take advantage of the optimized processing of the server.</span></span>  
  
 <span data-ttu-id="b72e6-107">데이터나 결과는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스 또는 SQL Server 데이터베이스에 보관하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-107">You do not have to keep your data or your results in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or in a SQL Server database.</span></span> <span data-ttu-id="b72e6-108">Excel 데이터 마이닝 추가 기능은 Excel에 저장된 데이터 또는 Excel 데이터 원본으로 연결하는 데이터에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-108">The Excel data mining add-ins can work with data stored only in Excel, or data that you connect to as an Excel data source.</span></span>  
  
## <a name="how-to-create-a-new-connection"></a><span data-ttu-id="b72e6-109">새 연결을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="b72e6-109">How to Create a New Connection</span></span>  
  
1.  <span data-ttu-id="b72e6-110">**연결** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-110">Click the **Connection** button.</span></span>  
  
2.  <span data-ttu-id="b72e6-111">**Analysis Services 연결** 대화 상자에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-111">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="b72e6-112">Analysis Services에 **연결** 대화 상자에서 서버 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-112">In the **Connect to Analysis Services** dialog box, type a server name.</span></span>  
  
4.  <span data-ttu-id="b72e6-113">인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-113">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="b72e6-114">데이터 마이닝 모델을 저장할 카탈로그나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-114">Specify the catalog, or [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, where you will store your data mining models.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b72e6-115">데이터베이스를 아직 만들지 않은 경우 (기본값)을 사용하여 데이터베이스를 만든 다음 연결을 테스트할 수 있습니다. 그러나 기본 연결에는 마이닝 모델을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-115">If you have not created any databases yet, you can use (default) to create and then test the connection; however, you cannot add mining models to the default connection.</span></span> <span data-ttu-id="b72e6-116">마이닝 모델을 만들려면 먼저 기존 데이터베이스에 대한 연결을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-116">Before you create any mining models, you should create a connection to an existing database.</span></span>  
  
6.  <span data-ttu-id="b72e6-117">웹 서비스를 통해 서버에 연결하는 경우 해당 웹 서비스에서 요구하는 사용자 이름과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-117">If you are connecting to the server via a Web service, type the user name and password required by the Web service.</span></span>  
  
7.  <span data-ttu-id="b72e6-118">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-118">Type a friendly name for the new connection.</span></span>  
  
8.  <span data-ttu-id="b72e6-119">**연결 테스트** 를 클릭 하 여 서버를 사용할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-119">Click **Test Connection** to verify that the server is available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="b72e6-120">연결 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b72e6-120">Troubleshooting Connections</span></span>  
 <span data-ttu-id="b72e6-121">이 섹션에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 연결에 대한 몇 가지 일반적인 질문에 대한 답변을 제시합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-121">This section provides answers to some common questions about connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b72e6-122">**"연결을 찾을 수 없습니다." 라는 메시지가 표시 됩니다.**</span><span class="sxs-lookup"><span data-stu-id="b72e6-122">**I get a message saying "No connection found."**</span></span>  
  
 <span data-ttu-id="b72e6-123">단추의 아래쪽에 있는 텍스트가 **연결 안 함**이라고 표시 되는 경우에는 데이터베이스에 대 한 연결을 만들지 않았거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 연결에 실패 했음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-123">If the text in the lower part of the button says **No Connection**, it means that you have not created a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or that the connection failed.</span></span> <span data-ttu-id="b72e6-124">Excel에서 Access을 비롯한 기타 원본의 데이터를 계속 사용할 수 있지만 데이터 마이닝 모델을 만들거나 예측 쿼리를 실행하려면 활성 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-124">You can continue to work with data in Excel from Access or other sources, but to create a data mining model or run a prediction query you must have an active connection.</span></span>  
  
 <span data-ttu-id="b72e6-125">**서버를 사용할 수 있는 권한이 없다고 가정해 보겠습니다.**</span><span class="sxs-lookup"><span data-stu-id="b72e6-125">**Suppose I don't have permission to use the server?**</span></span>  
  
 <span data-ttu-id="b72e6-126">서버에 마이닝 모델을 저장할 수 있는 권한이 없는 경우나 데이터 마이닝을 테스트하고 작업 내용을 저장하지는 않으려는 경우에는 테이블 분석 도구를 사용하여 임시 데이터 구조와 임시 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-126">If you do not have sufficient permissions to store your mining models on the server, or if you want to experiment with data mining and not save your work, you can use the Table Analysis Tools, which create temporary data structures and temporary models.</span></span> <span data-ttu-id="b72e6-127">여전히 서버에 임시 모델을 저장할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-127">You still need to be able to store temporary models on the server.</span></span> <span data-ttu-id="b72e6-128">서버에서 *세션 마이닝 모델* 을 사용할 수 있도록 관리자에 게 요청 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b72e6-128">Ask your administrator to enable use of *session mining models* on the server.</span></span>  
  
 <span data-ttu-id="b72e6-129">모델이 저장되도록 하려는 경우 임시 모델을 사용하는 옵션을 해제하거나 데이터 마이닝 클라이언트에서 마법사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-129">If you want to ensure that your models are saved, you can disable the option to use temporary models, or you can use the wizards in the Data Mining Client.</span></span> <span data-ttu-id="b72e6-130">이 마법사는 서버의 모든 모델을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-130">These wizards store all models on the server.</span></span> <span data-ttu-id="b72e6-131">모델이 저장된 데이터베이스에 대해 관리 액세스 권한이 필요하므로 관리자에게 특별히 추가 기능이 있는 마이닝 모델을 만들 수 있는 데이터베이스를 만들어 달라고 요청하십시오.</span><span class="sxs-lookup"><span data-stu-id="b72e6-131">You will need administrative access to the database where the models are stored, so we recommend that you get the administrator to create a database especially for creating mining models with the add-ins.</span></span>  
  
 <span data-ttu-id="b72e6-132">**연결이 끊어졌습니다. 작업이 모두 손실되나요?**</span><span class="sxs-lookup"><span data-stu-id="b72e6-132">**I lost my connection; did I lose all my work?**</span></span>  
  
 <span data-ttu-id="b72e6-133">서버에 대한 연결이 끊긴 경우 Excel에 저장되어 있으므로 결과 및 데이터가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-133">If you terminate the connection to the server, your results and data will not be lost, because they are stored in Excel.</span></span> <span data-ttu-id="b72e6-134">하지만 몇몇 임시 모델을 만든 경우에는 얼마 안 가서 서버에서 해당 모델이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-134">However, if you created some temporary models, those models will be deleted from the server after a short time.</span></span> <span data-ttu-id="b72e6-135">따라서 연결이 일시적으로 끊어진 경우에는 모델이 아직 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-135">So if you lose the connection temporarily, sometime the models won't be deleted yet.</span></span>  
  
 <span data-ttu-id="b72e6-136">모든 보고서와 테이블이 Excel에 저장되기 때문에 생성된 데이터나 결과가 전혀 손실되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-136">Any data or results that were generated will not be lost, because all reports and tables are stored in Excel.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b72e6-137">추가 기능이 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버와 통신하는 동안 서버나 네트워크에서 분리하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b72e6-137">Do not disconnect from the server or from the network while the add-in is communicating with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="b72e6-138">예를 들어 모델을 만들고 있거나 데이터를 처리하고 있을 때 연결을 끊으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-138">For example, never disconnect when a model is being created, or when the data is being processed.</span></span> <span data-ttu-id="b72e6-139">이러한 경우 연결을 끊으면 데이터가 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-139">In some situations your data could be corrupted.</span></span>  
  
 <span data-ttu-id="b72e6-140">**Visio 도구를 사용하여 모델에 연결할 수 없습니다.**</span><span class="sxs-lookup"><span data-stu-id="b72e6-140">**I cannot connect to the model using the Visio tools**</span></span>  
  
 <span data-ttu-id="b72e6-141">Visio용 데이터 마이닝 템플릿은 임시 마이닝 모델 및 구조를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-141">The Data Mining Templates for Visio cannot use temporary mining structures and models.</span></span> <span data-ttu-id="b72e6-142">마이닝 모델의 다이어그램을 만들려면 해당 모델이 서버에 저장되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-142">To create a diagram of a mining model, the model must be stored on a server.</span></span>  
  
 <span data-ttu-id="b72e6-143">**연결 사용을 모니터링하려면 어떻게 해야 합니까?**</span><span class="sxs-lookup"><span data-stu-id="b72e6-143">**How can I monitor usage of the connection?**</span></span>  
  
 <span data-ttu-id="b72e6-144">[Excel 용 데이터 마이닝 클라이언트&#41;&#40;추적](trace-data-mining-client-for-excel.md) 은 추가 기능과 지정 된 서버 간의 모든 동작에 대 한 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-144">The [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool creates a log of all activity between the add-ins and the specified server.</span></span>  
  
 <span data-ttu-id="b72e6-145">세션 모델의 모니터링을 사용 하도록 설정 하려면 **추적 프로그램** 대화 상자에서 **세션 모델 사용** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-145">To enable monitoring of session models, select the **Use session models** option in the **Tracer** dialog box.</span></span>  
  
 <span data-ttu-id="b72e6-146">이 추적을 사용하면 모델과 구조가 만들어지는 동안 생성된 DMX 및 XMLA 명령을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-146">The trace lets you view the DMX and XMLA commands generated while models and structures are being created.</span></span> <span data-ttu-id="b72e6-147">또한 Excel에서 결과와 보고서를 생성하기 위해 클라이언트에서 전송한 쿼리를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-147">You can also view the queries that are sent by the client to generate results and reports in Excel.</span></span>  
  
 <span data-ttu-id="b72e6-148">**임시 모델 이란? 임시 모델을 저장 하려면 어떻게 해야 하나요?**</span><span class="sxs-lookup"><span data-stu-id="b72e6-148">**What is a temporary model? How can I save a temporary model?**</span></span>  
  
 <span data-ttu-id="b72e6-149">Excel용 테이블 분석 도구는 기본적으로 임시 데이터 구조 및 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-149">The Table Analysis Tools for Excel by default creates temporary data structures and mining models.</span></span> <span data-ttu-id="b72e6-150">통합 문서가 열려 있고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 연결되어 있는 동안 계속해서 임시 모델을 찾아보고 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-150">You can continue to browse and query temporary models as long as you keep the workbook open and do not disconnect from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b72e6-151">Excel 통합 문서를 닫거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 연결을 변경 또는 종료하면 만들어진 구조 및 모델이 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-151">The structures and models that you have created will be deleted as soon as you close the Excel workbook, or if you change or end your connection to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b72e6-152">Excel용 데이터 마이닝 클라이언트에서 마법사를 완료하면 모델이 서버에 기본적으로 저장되지만, 각 마법사의 마지막 페이지에는 임시 모델을 사용하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-152">When you complete a wizard in the Data Mining Client for Excel, models are saved to the server by default, but on the final page of each wizard there is the option to use a temporary model.</span></span> <span data-ttu-id="b72e6-153">이 옵션을 선택하면 사용자가 만든 데이터 마이닝 구조 및 모델이 임시 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-153">If you select this option, the data mining structure and model that you created are stored in a temporary file.</span></span> <span data-ttu-id="b72e6-154">Excel이 열려 있는 동안 구조 및 모델을 찾아보기, 관리 및 수정할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="b72e6-154">You can browse, manage, and modify the structure and model as long as Excel remains open.</span></span> <span data-ttu-id="b72e6-155">Excel을 닫으면 구조와 관련 모델이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-155">However, once you close Excel, the structure and any related models are deleted.</span></span>  
  
 <span data-ttu-id="b72e6-156">**데이터 마이닝 고급 쿼리 편집기** 를 사용 하 고 DMX 템플릿 중 하나를 선택 하 여 임시 구조 또는 모델을 명시적으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-156">You can also explicitly create a temporary structure or model by using the **Data Mining Advanced Query Editor** and selecting one of the DMX templates.</span></span> <span data-ttu-id="b72e6-157">`USE SESSION MODELS` 절을 추가하여 해당 개체를 임시로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-157">Add the `USE SESSION MODELS` clause to specify that objects be temporary.</span></span>   
  
### <a name="creating-backups-of-mining-models-and-structures"></a><span data-ttu-id="b72e6-158">마이닝 모델 및 구조 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="b72e6-158">Creating Backups of Mining Models and Structures</span></span>  
 <span data-ttu-id="b72e6-159">모델 또는 구조의 백업을 만들려면 Excel 용 데이터 마이닝 클라이언트에서 모델 [관리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](manage-models-sql-server-data-mining-add-ins.md)을 사용 하 여 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-159">To create a backup of a model or structure, you can export it by using [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md), in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="b72e6-160">임시 마이닝 모델을 만든 경우 일반적으로 Table5_593679_TS_62446와 같이 이해 하기 어려운 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-160">If you created a temporary mining model, it typically has a name that is difficult to understand, such as Table5_593679_TS_62446.</span></span> <span data-ttu-id="b72e6-161">그러나 [Excel 용 데이터 마이닝 클라이언트&#41;도구로 추적 &#40;](trace-data-mining-client-for-excel.md) 를 사용 하 여 테이블 분석 도구에서 만든 임시 구조 및 모델의 이름을 검색 한 다음 **모델 관리**를 사용 하 여 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-161">However, you can use the [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool to discover the names of temporary structures and models that were created by the Table Analysis Tools and then back them up using **Manage Models**.</span></span>  
  
##### <a name="identify-and-export-a-temporary-model"></a><span data-ttu-id="b72e6-162">임시 모델 식별 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="b72e6-162">Identify and export a temporary model</span></span>  
  
1.  <span data-ttu-id="b72e6-163">Excel 용 데이터 마이닝 클라이언트의 **연결** 그룹에서 **추적**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-163">In the **Connections** group of the Data Mining Client for Excel, click **Trace**.</span></span>  
  
2.  <span data-ttu-id="b72e6-164">연결 활동 로그를 확인하고 열 및 예측 가능 결과(예)를 검토하여 모델을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-164">View the connection activity log, and locate the model by reviewing the columns and predictable outputs (for example).</span></span>  
  
     <span data-ttu-id="b72e6-165">고급 사용자: DMX 또는 XMLA에 대해 잘 알고 있는 경우 나중에 사용할 수 있도록 문을 파일에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-165">Advanced users: If you are familiar with DMX or XMLA, you can copy the statements to a file for later use.</span></span>  
  
3.  <span data-ttu-id="b72e6-166">임시 모델 및 구조의 이름을 찾았으면 **모델 관리** 를 열고 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-166">When you have found the name of the temporary model and structure, open **Manage Model** and select the model.</span></span>  
  
4.  <span data-ttu-id="b72e6-167">지정한 위치에서 스크립트 파일을 생성하려면 이 마이닝 모델 내보내기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b72e6-167">Click Export this mining model to generate a script file in a location you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72e6-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b72e6-168">See Also</span></span>  
 <span data-ttu-id="b72e6-169">[Excel 용 데이터 마이닝 클라이언트 &#40;원본 데이터에 연결&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b72e6-169">[Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span></span>  
 [<span data-ttu-id="b72e6-170">Excel 용 데이터 마이닝 추가 기능&#41;서버 구성 유틸리티 &#40;</span><span class="sxs-lookup"><span data-stu-id="b72e6-170">Server Configuration Utility &#40;Data Mining Add-ins for Excel&#41;</span></span>](server-configuration-utility-data-mining-add-ins-for-excel.md)  
  
  
