---
title: 데이터 원본 정의 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdf00b47360341e2b9a99654482d65be83b86503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639066"
---
# <a name="defining-a-data-source"></a><span data-ttu-id="2d76c-102">데이터 원본 정의</span><span class="sxs-lookup"><span data-stu-id="2d76c-102">Defining a Data Source</span></span>
  <span data-ttu-id="2d76c-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 만든 후 일반적으로 프로젝트에 사용할 하나 이상의 데이터 원본을 정의하여 프로젝트 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-103">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you generally start working with the project by defining one or more data sources that the project will use.</span></span> <span data-ttu-id="2d76c-104">데이터 원본을 정의하면 데이터 원본에 연결하는 데 사용할 연결 문자열 정보가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-104">When you define a data source, you are defining the connection string information that will be used to connect to the data source.</span></span> <span data-ttu-id="2d76c-105">자세한 내용은 [데이터 원본 만들기&#40;SSAS 다차원&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d76c-105">For more information, see [Create a Data Source &#40;SSAS Multidimensional&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md).</span></span>  
  
 <span data-ttu-id="2d76c-106">다음 태스크에서는 AdventureWorksDWSQLServer2012 예제 데이터베이스를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트의 데이터 원본으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-106">In the following task, you define the AdventureWorksDWSQLServer2012 sample database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="2d76c-107">이 자습서에서는 이 데이터베이스가 로컬 컴퓨터에 있지만 원본 데이터베이스는 대부분 하나 이상의 원격 컴퓨터에서 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-107">While this database is located on your local computer for the purposes of this tutorial, source databases are frequently hosted on one or more remote computers.</span></span>  
  
### <a name="to-define-a-new-data-source"></a><span data-ttu-id="2d76c-108">새 데이터 원본을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="2d76c-108">To define a new data source</span></span>  
  
1.  <span data-ttu-id="2d76c-109">Microsoft Visual Studio 창의 오른쪽에 있는 솔루션 탐색기에서 **데이터 원본**을 마우스 오른쪽 단추로 클릭하고 **새 데이터 원본**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Sources**, and then click **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="2d76c-110">**데이터 원본 마법사** 의 **데이터 원본 마법사 시작**페이지에서 **다음** 을 클릭하여 **연결 정의 방법 선택** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-110">On the **Welcome to the Data Source Wizard** page of the **Data Source Wizard**, click **Next** to open the **Select how to define the connection** page.</span></span>  
  
3.  <span data-ttu-id="2d76c-111">**연결 정의 방법 선택** 페이지에서 새 연결, 기존 연결 또는 이전에 정의한 데이터 원본 개체를 기반으로 데이터 원본을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-111">On the **Select how to define the connection** page, you can define a data source based on a new connection, based on an existing connection, or based on a previously defined data source object.</span></span> <span data-ttu-id="2d76c-112">이 자습서에서는 새 연결을 기반으로 데이터 원본을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-112">In this tutorial, you define a data source based on a new connection.</span></span> <span data-ttu-id="2d76c-113">**기존 연결 또는 새 연결을 사용하여 데이터 원본 만들기** 가 선택되어 있는지 확인한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-113">Verify that **Create a data source based on an existing or new connection** is selected, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2d76c-114">**연결 관리자** 대화 상자에서 데이터 원본에 대한 연결 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-114">In the **Connection Manager** dialog box, you define connection properties for the data source.</span></span> <span data-ttu-id="2d76c-115">**공급자** 목록 상자에서 **네이티브 OLE DB\SQL Server Native Client 11.0** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-115">In the **Provider** list box, verify that **Native OLE DB\SQL Server Native Client 11.0** is selected.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="2d76c-116">에서는 **공급자** 목록에 표시된 다른 공급자도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-116">also supports other providers, which are displayed in the **Provider** list.</span></span>  
  
5.  <span data-ttu-id="2d76c-117">**서버 이름** 텍스트 상자에을 입력 `localhost` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-117">In the **Server name** text box, type `localhost`.</span></span>  
  
     <span data-ttu-id="2d76c-118">로컬 컴퓨터의 명명 된 인스턴스에 연결 하려면 \*\*localhost \\<인스턴스 이름 \> \*\*을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-118">To connect to a named instance on your local computer, type **localhost\\<instance name\>**.</span></span> <span data-ttu-id="2d76c-119">로컬 컴퓨터 대신 특정 컴퓨터에 연결하려면 컴퓨터 이름 또는 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-119">To connect to the specific computer instead of the local computer, type the computer name or IP address.</span></span>  
  
6.  <span data-ttu-id="2d76c-120">**Windows 인증 사용** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-120">Verify that **Use Windows Authentication** is selected.</span></span> <span data-ttu-id="2d76c-121">**데이터베이스 이름 선택 또는 입력** 목록에서 **AdventureWorksDW2012**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-121">In the **Select or enter a database name** list, select **AdventureWorksDW2012**.</span></span>  
  
7.  <span data-ttu-id="2d76c-122">**연결 테스트** 를 클릭하여 데이터베이스에 대한 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-122">Click **Test Connection** to test the connection to the database.</span></span>  
  
8.  <span data-ttu-id="2d76c-123">**확인**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-123">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="2d76c-124">마법사의 **가장 정보** 페이지에서 데이터 원본 연결에 사용할 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 의 보안 자격 증명을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-124">On the **Impersonation Information** page of the wizard, you define the security credentials for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to use to connect to the data source.</span></span> <span data-ttu-id="2d76c-125">가장은 Windows 인증이 선택된 경우 데이터 원본에 연결하는 데 사용되는 Windows 계정에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-125">Impersonation affects the Windows account used to connect to the data source when Windows Authentication is selected.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="2d76c-126">에서는 OLAP 개체 처리를 위한 가장을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-126">does not support impersonation for processing OLAP objects.</span></span> <span data-ttu-id="2d76c-127">**서비스 계정 사용**을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-127">Select **Use the service account**, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="2d76c-128">**마법사 완료** 페이지에서 기본 이름인 **Adventure Works DW 2012**를 적용한 다음 **마침** 을 클릭하여 새 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-128">On the **Completing the Wizard** page, accept the default name, **Adventure Works DW 2012**, and then click **Finish** to create the new data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d76c-129">데이터 원본을 만든 후 속성을 수정하려면 **데이터 원본** 폴더에서 데이터 원본을 두 번 클릭하여 **데이터 원본 디자이너**에 데이터 원본 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d76c-129">To modify the properties of the data source after it has been created, double-click the data source in the **Data Sources** folder to display the data source properties in **Data Source Designer**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2d76c-130">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="2d76c-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2d76c-131">데이터 원본 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="2d76c-131">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d76c-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d76c-132">See Also</span></span>  
 [<span data-ttu-id="2d76c-133">데이터 원본 만들기&#40;SSAS 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="2d76c-133">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
  
