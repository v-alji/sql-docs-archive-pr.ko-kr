---
title: OLE DB 대상을 사용하여 데이터 로드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43e8d1123ae91d9e68c00fbe3e05c490383afe0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731935"
---
# <a name="load-data-by-using-the-ole-db-destination"></a><span data-ttu-id="92d00-102">OLE DB 대상을 사용하여 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="92d00-102">Load Data by Using the OLE DB Destination</span></span>
  <span data-ttu-id="92d00-103">OLE DB 대상을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-103">To add and configure an OLE DB destination, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-load-data-using-an-ole-db-destination"></a><span data-ttu-id="92d00-104">OLE DB 대상을 사용하여 데이터를 로드하려면</span><span class="sxs-lookup"><span data-stu-id="92d00-104">To load data using an OLE DB destination</span></span>  
  
1.  <span data-ttu-id="92d00-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="92d00-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="92d00-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 OLE DB 대상을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="92d00-108">데이터 원본 또는 이전 변환에서 연결선을 대상으로 끌어 와서 OLE DB 대상을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-108">Connect the OLE DB destination to the data flow by dragging a connector from a data source or a previous transformation to the destination.</span></span>  
  
5.  <span data-ttu-id="92d00-109">OLE DB 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-109">Double-click the OLE DB destination.</span></span>  
  
6.  <span data-ttu-id="92d00-110">**OLE DB 대상 편집기** 대화 상자의 **연결 관리자** 페이지에서 기존 OLE DB 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-110">In the **OLE DB Destination Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="92d00-111">자세한 내용은 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d00-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="92d00-112">다음과 같은 데이터 액세스 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-112">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="92d00-113">**테이블 또는 뷰** 데이터베이스에서 데이터가 포함된 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-113">**Table or view** Select a table or view in the database that contains the data.</span></span>  
  
    -   <span data-ttu-id="92d00-114">**테이블 또는 뷰 - 빠른 로드** 데이터베이스에서 데이터가 포함된 테이블 또는 뷰를 선택한 후에 **ID 유지**, **Null 유지**, **테이블 잠금**, **CHECK 제약 조건**, **일괄 처리당 행 수**또는 **최대 삽입 커밋 크기**중에서 빠른 로드 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-114">**Table or view - fast load** Select a table or view in the database that contains the data, and then set the fast-load options: **Keep identity**, **Keep null**, **Table lock**, **Check constraint**, **Rows per batch**, or **Maximum insert commit size**.</span></span>  
  
    -   <span data-ttu-id="92d00-115">**테이블 이름 또는 뷰 이름 변수** 데이터베이스의 테이블 또는 뷰 이름이 포함된 사용자 정의 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-115">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database.</span></span>  
  
    -   <span data-ttu-id="92d00-116">**테이블 이름 또는 뷰 이름 변수 - 빠른 로드** 데이터베이스에서 데이터가 포함된 테이블 또는 뷰의 이름이 포함된 사용자 정의 변수를 선택한 후 빠른 로드 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-116">**Table name or view name variable fast load** Select the user-defined variable that contains the name of a table or view in the database that contains the data, and then set the fast-load options.</span></span>  
  
    -   <span data-ttu-id="92d00-117">**SQL 명령** SQL 명령을 입력하거나 **쿼리 작성** 을 클릭하고 **쿼리 작성기**를 사용하여 SQL 명령을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-117">**SQL command** Type an SQL command or click **Build Query** to write an SQL command by using the **Query Builder**.</span></span>  
  
8.  <span data-ttu-id="92d00-118">**매핑** 을 클릭한 후 **사용 가능한 입력 열** 목록의 열을 **사용 가능한 대상 열** 목록의 열로 끌어서 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-118">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="92d00-119">OLE DB 대상은 같은 이름의 열로 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-119">The OLE DB destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="92d00-120">오류 출력을 구성하려면 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-120">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="92d00-121">자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d00-121">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="92d00-122">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="92d00-123">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92d00-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d00-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92d00-124">See Also</span></span>  
 <span data-ttu-id="92d00-125">[OLE DB 대상](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="92d00-125">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="92d00-126">[Integration Services 변환](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="92d00-126">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="92d00-127">[Integration Services 경로](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="92d00-127">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="92d00-128">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="92d00-128">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
