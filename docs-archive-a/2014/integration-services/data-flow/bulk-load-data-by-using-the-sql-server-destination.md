---
title: SQL Server 대상을 사용하여 데이터 대량 로드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 92ed530ae849f7a4ce123cded421ac0cd0c411ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650214"
---
# <a name="bulk-load-data-by-using-the-sql-server-destination"></a><span data-ttu-id="f8b7b-102">SQL Server 대상을 사용하여 데이터 대량 로드</span><span class="sxs-lookup"><span data-stu-id="f8b7b-102">Bulk Load Data by Using the SQL Server Destination</span></span>
  <span data-ttu-id="f8b7b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 데이터 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-103">To add and configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, the package must already include at least one Data Flow task and a data source.</span></span>  
  
### <a name="to-load-data-using-a-sql-server-destination"></a><span data-ttu-id="f8b7b-104">SQL Server 대상을 사용하여 데이터를 로드하려면</span><span class="sxs-lookup"><span data-stu-id="f8b7b-104">To load data using a SQL Server destination</span></span>  
  
1.  <span data-ttu-id="f8b7b-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f8b7b-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f8b7b-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="f8b7b-108">연결선을 대상으로 끌어 와서 대상을 데이터 흐름에 있는 원본 또는 이전 변환에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-108">Connect the destination to a source or a previous transformation in the data flow by dragging a connector to the destination.</span></span>  
  
5.  <span data-ttu-id="f8b7b-109">대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-109">Double-click the destination.</span></span>  
  
6.  <span data-ttu-id="f8b7b-110">**SQL Server 대상 편집기**의 **연결 관리자** 페이지에서 기존 OLE DB 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-110">In the **SQL Server Destination Editor**, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="f8b7b-111">자세한 내용은 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="f8b7b-112">데이터를 로드할 테이블 또는 뷰를 지정하려면 다음 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-112">To specify the table or view into which to load the data, do one of the following:</span></span>  
  
    -   <span data-ttu-id="f8b7b-113">기존 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-113">Select an existing table or view.</span></span>  
  
    -   <span data-ttu-id="f8b7b-114">**새로 만들기**를 클릭하고 **테이블 만들기** 대화 상자에서 테이블 또는 뷰를 만드는 SQL 문을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-114">Click **New**, and in the **Create Table** dialog boxwrite an SQL statement that creates a table or view.</span></span>  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="f8b7b-115">는 연결된 데이터 원본에 따라 기본 CREATE TABLE 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-115">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="f8b7b-116">원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="f8b7b-117">FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-117">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="f8b7b-118">그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="f8b7b-119">자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="f8b7b-120">**매핑** 을 클릭하고 **사용 가능한 입력 열** 목록의 열을 **사용 가능한 대상 열** 목록의 열로 끌어서 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-120">Click **Mappings** and map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8b7b-121">대상은 같은 이름의 열로 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-121">The destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="f8b7b-122">**고급** 을 클릭하고 **ID 유지**, **Null 유지**, **테이블 잠금**, **CHECK 제약 조건**및 **트리거 실행**과 같은 대량 로드 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-122">Click **Advanced** and set the bulk load options: **Keep identity**, **Keep nulls**, **Table lock**, **Check constraints**, and **Fire triggers**.</span></span>  
  
     <span data-ttu-id="f8b7b-123">선택적으로 삽입할 첫 번째와 마지막 입력 행, 삽입 작업이 중지되기 전에 발생할 수 있는 최대 오류 개수 및 삽입이 정렬될 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-123">Optionally, specify the first and last input rows to insert, the maximum number of errors that can occur before the insert operation stops, and the columns on which the insert is sorted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8b7b-124">정렬 순서는 열이 나열되는 순서에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-124">The sort order is determined by the order in which the columns are listed.</span></span>  
  
10. <span data-ttu-id="f8b7b-125">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-125">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f8b7b-126">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b7b-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b7b-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8b7b-127">See Also</span></span>  
 <span data-ttu-id="f8b7b-128">[SQL Server Destination](sql-server-destination.md) </span><span class="sxs-lookup"><span data-stu-id="f8b7b-128">[SQL Server Destination](sql-server-destination.md) </span></span>  
 <span data-ttu-id="f8b7b-129">[Integration Services 변환](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="f8b7b-129">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="f8b7b-130">[Integration Services 경로](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="f8b7b-130">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="f8b7b-131">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="f8b7b-131">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
