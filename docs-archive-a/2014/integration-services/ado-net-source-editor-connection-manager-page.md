---
title: ADO NET 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19dd9c256f15bc9022f7267cb38b6f91bd4d8a5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736682"
---
# <a name="ado-net-source-editor-connection-manager-page"></a><span data-ttu-id="cc697-102">ADO NET 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="cc697-102">ADO NET Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="cc697-103">**ADO NET 원본 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 원본의 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-103">Use the **Connection Manager** page of the **ADO NET Source Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the source.</span></span> <span data-ttu-id="cc697-104">이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="cc697-105">ADO NET 원본에 대한 자세한 내용은 [ADO NET Source](data-flow/ado-net-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc697-105">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="cc697-106">**연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="cc697-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="cc697-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 ADO NET 원본이 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="cc697-108">**데이터 흐름** 탭에서 ADO NET 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-108">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="cc697-109">**ADO NET 원본 편집기**에서 **연결 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-109">In the **ADO NET Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="cc697-110">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="cc697-110">Static Options</span></span>  
 <span data-ttu-id="cc697-111">**ADO.NET 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="cc697-111">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="cc697-112">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="cc697-113">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="cc697-113">**New**</span></span>  
 <span data-ttu-id="cc697-114">**ADO.NET 연결 관리자 구성** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="cc697-115">**데이터 액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="cc697-115">**Data access mode**</span></span>  
 <span data-ttu-id="cc697-116">원본에서 데이터를 선택하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-116">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="cc697-117">옵션</span><span class="sxs-lookup"><span data-stu-id="cc697-117">Option</span></span>|<span data-ttu-id="cc697-118">Description</span><span class="sxs-lookup"><span data-stu-id="cc697-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cc697-119">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="cc697-119">Table or view</span></span>|<span data-ttu-id="cc697-120">[!INCLUDE[vstecado](../includes/vstecado-md.md)] 데이터 원본에 있는 테이블이나 뷰에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-120">Retrieve data from a table or view in the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source.</span></span>|  
|<span data-ttu-id="cc697-121">SQL 명령</span><span class="sxs-lookup"><span data-stu-id="cc697-121">SQL command</span></span>|<span data-ttu-id="cc697-122">SQL 쿼리를 사용하여 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 데이터 원본에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-122">Retrieve data from the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source by using a SQL query.</span></span>|  
  
 <span data-ttu-id="cc697-123">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="cc697-123">**Preview**</span></span>  
 <span data-ttu-id="cc697-124">**데이터 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-124">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="cc697-125">**미리 보기** 에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-125">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc697-126">데이터를 미리 보면 CLR 사용자 정의 형식의 열에 데이터가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-126">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="cc697-127">대신 \<value too big to display> 또는 System.Byte[] 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-127">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="cc697-128">전자는 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 공급자를 사용하여 데이터 원본에 액세스하는 경우 표시되고 후자는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 공급자를 사용하는 경우 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-128">The former displays when the data source is accessed by using the [!INCLUDE[vstecado](../includes/vstecado-md.md)] provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="cc697-129">데이터 액세스 모드 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="cc697-129">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="cc697-130">데이터 액세스 모드 = 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="cc697-130">Data access mode = Table or view</span></span>  
 <span data-ttu-id="cc697-131">**테이블 또는 뷰 이름**</span><span class="sxs-lookup"><span data-stu-id="cc697-131">**Name of the table or the view**</span></span>  
 <span data-ttu-id="cc697-132">데이터 원본의 사용 가능한 테이블 또는 뷰 목록에서 테이블 또는 뷰 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-132">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="cc697-133">데이터 액세스 모드 = SQL 명령</span><span class="sxs-lookup"><span data-stu-id="cc697-133">Data access mode = SQL command</span></span>  
 <span data-ttu-id="cc697-134">**SQL 명령 텍스트**</span><span class="sxs-lookup"><span data-stu-id="cc697-134">**SQL command text**</span></span>  
 <span data-ttu-id="cc697-135">SQL 쿼리 텍스트를 입력하고 **쿼리 작성**을 클릭하여 쿼리를 작성하거나 **찾아보기**를 클릭하여 쿼리 텍스트가 포함된 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-135">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="cc697-136">**쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="cc697-136">**Build query**</span></span>  
 <span data-ttu-id="cc697-137">**쿼리 작성기** 대화 상자를 사용하여 시각적으로 SQL 쿼리를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-137">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="cc697-138">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="cc697-138">**Browse**</span></span>  
 <span data-ttu-id="cc697-139">**열기** 대화 상자를 사용하여 SQL 쿼리 텍스트가 포함된 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc697-139">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc697-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc697-140">See Also</span></span>  
 <span data-ttu-id="cc697-141">[ADO NET 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="cc697-141">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="cc697-142">[ADO NET 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="cc697-142">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="cc697-143">ADO.NET 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="cc697-143">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
