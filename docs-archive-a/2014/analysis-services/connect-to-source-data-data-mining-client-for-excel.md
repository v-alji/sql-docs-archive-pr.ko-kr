---
title: 원본 데이터에 연결 (Excel 용 데이터 마이닝 클라이언트) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4b4759d94043fdccacdf5b285de50697a18965e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647994"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a><span data-ttu-id="91c17-102">원본 데이터에 연결(Excel용 데이터 마이닝 클라이언트)</span><span class="sxs-lookup"><span data-stu-id="91c17-102">Connect to Source Data (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="91c17-103">이 항목에서는 데이터 마이닝 모델 저장 및 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 저장된 외부 데이터 액세스용 연결을 만들고 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-103">This topic describes how to create and use connections used for storing data mining models, and for accessing external data stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="91c17-104">**데이터 마이닝 연결.**</span><span class="sxs-lookup"><span data-stu-id="91c17-104">**Data mining connections.**</span></span> <span data-ttu-id="91c17-105">추가 기능을 시작할 때 만드는 초기 연결은 알고리즘 액세스, 데이터 분석, 마이닝 구조 및 모델 저장에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-105">The initial connection that you create when you start the add-ins is used to access algorithms, analyze data, and store mining structure and models.</span></span>  
  
 <span data-ttu-id="91c17-106">추가 기능에는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 제공하는 알고리즘 및 데이터 구조가 필요하므로 모델링 및 시각화 도구를 사용하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-106">A connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is required to use the modeling and visualization tools in the add-ins, because the add-ins depend on algorithms and data structures that are provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="91c17-107">**외부 데이터 원본 연결.**</span><span class="sxs-lookup"><span data-stu-id="91c17-107">**Connections to external data sources.**</span></span> <span data-ttu-id="91c17-108">모델을 작성하거나 결과를 저장할 때 외부 데이터에 대한 연결을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-108">You can also create connections to external data as you are building models or saving the results.</span></span> <span data-ttu-id="91c17-109">예를 들어 한 서버에 데이터 마이닝 모델을 만든 다음 다른 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스, Excel 데이터 테이블 또는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access와 같은 외부 데이터 원본에 저장된 데이터를 사용하여 이 데이터 마이닝 모델에 대한 예측 쿼리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-109">For example, you can create a data mining model on one server, and then perform a prediction query against the data mining model by using data stored in another instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], in an Excel data table, or in an external data source such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Access.</span></span> <span data-ttu-id="91c17-110">새 데이터 원본에 액세스할 때마다 대화 상자를 사용하여 연결을 만들라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-110">Each time that you access a new data source, you will be prompted to create a connection by using a dialog box.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq2"></a> <span data-ttu-id="91c17-111">필수 조건</span><span class="sxs-lookup"><span data-stu-id="91c17-111">Prerequisites</span></span>  
 <span data-ttu-id="91c17-112">이 버전의 추가 기능을 사용하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스가 SQL Server 2012여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-112">This version of the add-ins requires that your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] be SQL Server 2012.</span></span> <span data-ttu-id="91c17-113">개별 버전의 추가 기능을 사용하여 이전 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-113">A separate version of the add-ins is available if you want to connect to an earlier version of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="91c17-114">SQL Server 2005, SQL Server 2008 및 SQL Server 2008 R2를 지원하는 추가 기능 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-114">There are versions of the add-ins that support SQL Server 2005, SQL Server 2008, and SQL Server 2008 R2.</span></span>  
  
 <span data-ttu-id="91c17-115">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 연결하려면 해당 데이터베이스 서버에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-115">To connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, you must have permissions to access the database server.</span></span> <span data-ttu-id="91c17-116">또한 데이터 마이닝 세션이 활성화되어야 하며 서버에 저장된 데이터베이스 개체에 대한 읽기 또는 읽기/쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-116">Moreover, data mining sessions must be enabled, and you must have read or read/write permissions on database objects stored on the server.</span></span>  
  
##  <a name="creating-data-mining-server-connections"></a><a name="bkmk_connect"></a><span data-ttu-id="91c17-117">데이터 마이닝 서버 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="91c17-117">Creating Data Mining Server Connections</span></span>  
 <span data-ttu-id="91c17-118">Excel 용 데이터 마이닝 클라이언트 및 Excel 용 테이블 분석 도구에 있는 **연결** 그룹에서는 인스턴스에 대 한 연결을 관리 하기 위한 도구를 제공 합니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="91c17-118">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel provides tools for managing connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="91c17-119">추가 기능을 설치할 때 연결을 만들거나 나중에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-119">You can create the connection when you install the add-in, or you can add a connection later.</span></span>  
  
-   <span data-ttu-id="91c17-120">모델을 만들거나 쿼리하는 중이 아니면 언제든지 여러 연결을 만들고 연결을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-120">You can create multiple connections, and change connections at any time, unless you are in the process of creating or querying a model.</span></span>  
  
     <span data-ttu-id="91c17-121">데이터 마이닝 모델을 처리하는 동안에는 연결을 변경하거나 닫지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="91c17-121">Do not change or close a connection when a data mining model is being processed.</span></span> <span data-ttu-id="91c17-122">데이터 마이닝 모델의 데이터가 손실되거나 모델을 사용할 수 없게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-122">The data mining model might lose data, or the model might become unusable.</span></span>  
  
-   <span data-ttu-id="91c17-123">특정 시간에 하나의 연결만 활성화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-123">Only one connection can be active at a particular time.</span></span>  
  
### <a name="connections-in-the-excel-add-ins"></a><span data-ttu-id="91c17-124">Excel 추가 기능에서 연결</span><span class="sxs-lookup"><span data-stu-id="91c17-124">Connections in the Excel Add-ins</span></span>  
 <span data-ttu-id="91c17-125">Excel 용 데이터 마이닝 클라이언트 및 Excel 용 테이블 분석 도구에 있는 **연결** 그룹에서는 인스턴스에 대 한 연결을 관리 합니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="91c17-125">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel is where you manage connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a><span data-ttu-id="91c17-126">Excel 추가 기능에서 새 서버 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="91c17-126">Create a new server connection in the Excel add-ins</span></span>  
  
1.  <span data-ttu-id="91c17-127">**분석** 또는 **데이터 마이닝** 리본에서 **연결** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-127">Click the **Connection** button on the **Analyze** or **Data Mining** ribbon.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91c17-128">단추의 텍스트는 연결이 존재하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-128">The text of the button indicates if a connection exists.</span></span> <span data-ttu-id="91c17-129">워크시트에 연결 되지 않은 경우 단추에는 "." 라는 텍스트가 포함 \<No connection> 됩니다. 이전에 통합 문서에서 연결을 만든 경우 해당 연결의 이름이 단추에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-129">When no connection has been made in the worksheet, the button contains the text "\<No connection>." If a connection was previously made in the workbook, the name of that connection appears in the button.</span></span>  
  
2.  <span data-ttu-id="91c17-130">**Analysis Services 연결** 대화 상자에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-130">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="91c17-131">**새 Analysis Services 연결** 대화 상자에서 서버 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-131">In the **New Analysis Services Connection** dialog box, type the name of the server.</span></span>  
  
4.  <span data-ttu-id="91c17-132">인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-132">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="91c17-133">**카탈로그 이름** 드롭다운 목록에서 데이터베이스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-133">Select a database from the **Catalog name** drop-down list.</span></span> <span data-ttu-id="91c17-134">인스턴스에 데이터베이스가 없는 경우 **(기본값)** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-134">If no database exists on the instance, select **(default)**.</span></span>  
  
6.  <span data-ttu-id="91c17-135">연결에 대한 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-135">Type a friendly name for the connection.</span></span>  
  
7.  <span data-ttu-id="91c17-136">**연결 테스트** 를 클릭 하 여 서버 및 데이터베이스를 사용할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-136">Click **Test Connection** to verify that the server and database are available.</span></span>  
  
8.  <span data-ttu-id="91c17-137">**확인**을 클릭하고 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-137">Click **OK**, and then click **Close**.</span></span>  
  
### <a name="connections-using-a-web-service"></a><span data-ttu-id="91c17-138">웹 서비스를 사용하여 연결</span><span class="sxs-lookup"><span data-stu-id="91c17-138">Connections using a Web Service</span></span>  
 <span data-ttu-id="91c17-139">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브 및 데이터에 대한 찾아보기 기능을 활성화하는 씬 클라이언트 아키텍처를 사용할 경우에는 웹 서비스를 통해 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 대한 연결을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-139">If you are using a thin-client architecture to enable browsing of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cubes and data, you can also configure a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server through Web services.</span></span> <span data-ttu-id="91c17-140">웹 기반 클라이언트를 정의하는 방법은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="91c17-140">For information about how to define a Web-based client, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="91c17-141">웹 서비스용으로 구성된 서버에 대한 액세스 권한이 있다면 처음 연결을 만들 때 연결 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-141">If you have access to a server that has been configured for Web services, you can specify the connection type when you first create the connection.</span></span>  
  
##### <a name="create-an-http-connection-to-analysis-services"></a><span data-ttu-id="91c17-142">Analysis Services에 대한 HTTP 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="91c17-142">Create an HTTP connection to Analysis Services</span></span>  
  
1.  <span data-ttu-id="91c17-143">**새 Analysis Services 연결** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-143">Open the **New Analysis Services Connection** dialog box.</span></span>  
  
2.  <span data-ttu-id="91c17-144">서버 이름에는 http:// 다음 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 할당된 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-144">For the server name, type http:// followed by the URL assigned to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span>  
  
3.  <span data-ttu-id="91c17-145">웹 서비스에 액세스하는 데 필요한 사용자 이름과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-145">Type the user name and the password that is required to access the Web service.</span></span>  
  
### <a name="connections-in-the-visio-add-in"></a><span data-ttu-id="91c17-146">Visio 추가 기능에서 연결</span><span class="sxs-lookup"><span data-stu-id="91c17-146">Connections in the Visio Add-In</span></span>  
 <span data-ttu-id="91c17-147">Visio는 Excel과는 달리 도구 리본을 제공하지 않으며 연결 설정 또는 모니터링을 위한 단추가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-147">Unlike Excel, Visio does not provide a tool ribbon, and there are no buttons specifically for creating or monitoring connections.</span></span> <span data-ttu-id="91c17-148">대신 처음으로 데이터 마이닝 셰이프를 선택하여 Visio 페이지로 끌어 놓을 때 데이터 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-148">Instead, the data connection is created when you first select a data mining shape and drop it onto a Visio page.</span></span> <span data-ttu-id="91c17-149">셰이프 모델을 선택하고 기타 옵션을 설정하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-149">A wizard will prompt you to select the model for the shape and to set other options.</span></span>  
  
 <span data-ttu-id="91c17-150">Excel에서 이전에 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본에 대한 연결을 사용한 경우 해당 연결이 선택 가능한 데이터 원본으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-150">If you have previously used a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source in Excel, these connections are listed as possible data sources from which to select.</span></span>  
  
##### <a name="create-a-connection-for-a-visio-shape"></a><span data-ttu-id="91c17-151">Visio 셰이프에 대한 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="91c17-151">Create a connection for a Visio shape</span></span>  
  
1.  <span data-ttu-id="91c17-152">데이터 마이닝 템플릿을 열고 데이터 마이닝 셰이프 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-152">Open the Data Mining Template, and select one of the data mining shapes.</span></span>  
  
2.  <span data-ttu-id="91c17-153">셰이프를 빈 페이지로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-153">Drag and drop the shape to a blank page.</span></span>  
  
3.  <span data-ttu-id="91c17-154">**데이터 원본 선택** 대화 상자의 목록에서 데이터 원본을 선택 하거나 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-154">In the **Select a data source** dialog box, select a data source from the list, or click **New**.</span></span>  
  
4.  <span data-ttu-id="91c17-155">**새로 만들기**를 선택 하는 경우 앞에서 설명한 절차에 따라 서버 및 카탈로그 이름을 지정 하거나 웹 서비스를 통해 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-155">If you select **New**, follow the procedure that is described earlier to specify a server and catalog name, or to connect through a Web service.</span></span>  
  
##  <a name="changing-connections"></a><a name="bkmk_change"></a><span data-ttu-id="91c17-156">연결 변경</span><span class="sxs-lookup"><span data-stu-id="91c17-156">Changing Connections</span></span>  
 <span data-ttu-id="91c17-157">동일한 워크시트 내에 여러 개의 연결을 만들 수 있지만 한 번에 한 연결만 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-157">You can create multiple connections in the same worksheet, but only one connection can be active at a time.</span></span> <span data-ttu-id="91c17-158">현재 연결의 이름이 **연결** 단추에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-158">The name of the current connection is displayed in the **Connection** button.</span></span>  
  
 <span data-ttu-id="91c17-159">Excel 용 데이터 마이닝 클라이언트에서 **추적** 을 클릭 한 다음 **현재 연결**을 클릭 하 여 현재 연결에 대 한 연결 문자열 및 상태를 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-159">In the Data Mining Client for Excel, you can also verify the connection string and status for the current connection by clicking **Trace** and then clicking **Current Connection**.</span></span>  
  
#### <a name="use-a-different-server-connection"></a><span data-ttu-id="91c17-160">다른 서버 연결 사용</span><span class="sxs-lookup"><span data-stu-id="91c17-160">Use a different server connection</span></span>  
  
1.  <span data-ttu-id="91c17-161">**연결**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-161">Click **Connection**.</span></span>  
  
2.  <span data-ttu-id="91c17-162">**Analysis Services 연결** 창의 **다른 연결** 목록에서 연결을 선택 하 고 **현재 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-162">In the **Analysis Services Connections** pane, select a connection from the **Other Connections** list, and click **Make Current**.</span></span>  
  
3.  <span data-ttu-id="91c17-163">**연결 테스트** 를 클릭 하 여 연결을 사용할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-163">Click **Test Connection** to verify that the connection is available.</span></span>  
  
 <span data-ttu-id="91c17-164">마이닝 모델 처리를 완료하면 결과는 로컬로 저장되며 한 서버에 대한 연결을 닫고 다른 서버에 연결하면 데이터에는 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-164">After a mining model has finished processing, the results are stored locally, and there is no effect on the data if you close the connection to one server and then connect to another server.</span></span> <span data-ttu-id="91c17-165">그러나 데이터가 손상될 수 있으므로 데이터 마이닝 모델이 처리되고 있는 동안에는 연결을 변경 또는 해제하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-165">However, you should avoid changing connections or losing the connection when a data mining model is being processed, because this could corrupt data.</span></span>  
  
#### <a name="modify-an-existing-server-connection"></a><span data-ttu-id="91c17-166">기존 서버 연결 수정</span><span class="sxs-lookup"><span data-stu-id="91c17-166">Modify an existing server connection</span></span>  
  
1.  <span data-ttu-id="91c17-167">다른 데이터베이스나 서버에 연결하려는 경우 기존 연결을 변경할 수 없으며 새 연결을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-167">You cannot modify an existing connection; if you want to connect to a different database or a different server, you should create a new connection.</span></span>  
  
2.  <span data-ttu-id="91c17-168">연결 문자열을 수정하여 쿼리 제한 시간을 늘리거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스와 관련된 다른 매개 변수를 추가해야 하는 경우 한 가지 옵션은 연결 문자열이 저장되는 .dmc 파일을 편집하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-168">If you must modify the connection string to increase the query timeout or add other parameters specific to your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], one option is to edit the .dmc file, where the connection string is stored.</span></span>  
  
     <span data-ttu-id="91c17-169">\<drive:>\Users \\<myusername \> \AppData\Local\Microsoft\Data 마이닝 추가 기능</span><span class="sxs-lookup"><span data-stu-id="91c17-169">\<drive:>\Users\\<myusername\>\AppData\Local\Microsoft\Data Mining Add-in</span></span>  
  
##  <a name="connecting-to-external-data-sources"></a><a name="bkmk_extconnections"></a><span data-ttu-id="91c17-170">외부 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="91c17-170">Connecting to External Data Sources</span></span>  
 <span data-ttu-id="91c17-171">**분석** 리본의 도구는 Excel의 데이터로만 작동 하지만 **데이터 마이닝** 리본의 도구를 사용 하면 외부 데이터 원본에 직접 연결 하 여 모델에 대 한 입력으로 사용 하거나 샘플링을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-171">Whereas the tools in the **Analyze** ribbon work exclusively with data in Excel, the tools in the **Data Mining** ribbon let you connect directly to external data sources to use as inputs for your model, or for sampling.</span></span>  
  
 <span data-ttu-id="91c17-172">이러한 추가 기능의 다음과 같은 도구가 데이터 마이닝에 외부 데이터를 사용할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-172">The following tools in these add-ins support use of external data for data mining:</span></span>  
  
-   [<span data-ttu-id="91c17-173">데이터 마이닝 추가 기능을 SQL Server &#40;샘플 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-173">Sample Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="91c17-174">분류 마법사 &#40;Excel 용 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-174">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="91c17-175">Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-175">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="91c17-176">클러스터 마법사는 Excel 용 데이터 마이닝 추가 기능을 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-176">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="91c17-177">Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-177">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="91c17-178">데이터 마이닝 추가 기능을 SQL Server &#40;마이닝 구조를 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-178">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="91c17-179">정확도 차트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-179">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="91c17-180">수익 차트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-180">Profit Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="91c17-181">분류표는 데이터 마이닝 추가 기능을 SQL Server &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="91c17-181">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a><span data-ttu-id="91c17-182">Analysis Services를 데이터 원본으로 사용</span><span class="sxs-lookup"><span data-stu-id="91c17-182">Using Analysis Services as a Data Source</span></span>  
 <span data-ttu-id="91c17-183">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브나 테이블 형식 모델에 저장된 데이터에는 직접 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-183">You cannot directly access data stored in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube or tabular model.</span></span> <span data-ttu-id="91c17-184">대신 Excel에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 대한 연결을 만들고 데이터를 사용하여 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-184">Instead, create a connection in Excel to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and use the data to create a model.</span></span>  
  
### <a name="relational-data-sources"></a><span data-ttu-id="91c17-185">관계형 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="91c17-185">Relational Data Sources</span></span>  
 <span data-ttu-id="91c17-186">관계형 원본의 데이터를 모델에 대한 입력으로 사용하려는 경우 다음 버전의 SQL Server에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-186">If you want to use data from a relational source as input to your model, you can connect to the following versions of SQL Server:</span></span>  
  
-   <span data-ttu-id="91c17-187">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="91c17-187">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="91c17-188">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="91c17-188">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="91c17-189">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="91c17-189">SQL Server 2012</span></span>  
  
 <span data-ttu-id="91c17-190">또한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 데이터 원본으로 지원하는 다른 관계형 데이터 원본에서 데이터를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-190">You can also get data from any other relational data source that is supported as a data source by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="91c17-191">지원 되는 데이터 원본에 대 한 자세한 내용은 [다차원 모델의 데이터 원본](multidimensional-models/data-sources-in-multidimensional-models.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="91c17-191">For information about supported data sources, see [Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md)</span></span>  
  
 <span data-ttu-id="91c17-192">다음 데이터 형식은 데이터 마이닝에 사용할 수 없으며 모델 작성 시 포함될 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c17-192">Note that the following data types cannot be used for data mining and will result in an error if included when you build a model:</span></span>  
  
-   <span data-ttu-id="91c17-193">ntext</span><span class="sxs-lookup"><span data-stu-id="91c17-193">ntext</span></span>  
  
-   <span data-ttu-id="91c17-194">binary</span><span class="sxs-lookup"><span data-stu-id="91c17-194">binary</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c17-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91c17-195">See Also</span></span>  
 [<span data-ttu-id="91c17-196">Excel 용 데이터 마이닝 클라이언트&#41;추적 &#40;</span><span class="sxs-lookup"><span data-stu-id="91c17-196">Trace &#40;Data Mining Client for Excel&#41;</span></span>](trace-data-mining-client-for-excel.md)  
  
  
