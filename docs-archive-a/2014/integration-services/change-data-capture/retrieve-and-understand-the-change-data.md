---
title: 변경 데이터 검색 및 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62f60bf4a79c39b4f0cb7d1ba8fb3f52680a1f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735516"
---
# <a name="retrieve-and-understand-the-change-data"></a><span data-ttu-id="69b1c-102">변경 데이터 검색 및 이해</span><span class="sxs-lookup"><span data-stu-id="69b1c-102">Retrieve and Understand the Change Data</span></span>
  <span data-ttu-id="69b1c-103">변경 데이터를 증분 로드하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 데이터 흐름에서 첫 번째 태스크는 변경 데이터를 검색하는 쿼리를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to run the query that retrieves the change data.</span></span> <span data-ttu-id="69b1c-104">데이터 흐름 태스크의 원본 구성 요소 내에서 이 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-104">You execute this query inside a source component in a Data Flow task.</span></span> <span data-ttu-id="69b1c-105">그런 다음 다운스트림 변환 및 대상을 사용하여 대상에 변경 데이터를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-105">You can then use downstream transformations and destinations to apply the change data to your destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69b1c-106">테이블 반환 함수를 포함하는 쿼리 생성 작업은 변경 데이터를 증분 로드하는 패키지 생성 프로세스의 세 번째 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-106">The creation of a query that contains a table-valued function is the third step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="69b1c-107">이 쿼리에 대한 자세한 내용은 [변경 데이터 검색을 위한 함수 만들기](create-the-function-to-retrieve-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b1c-107">For more information about this query, see, [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span> <span data-ttu-id="69b1c-108">변경 데이터를 증분 로드하는 패키지를 만드는 전체 프로세스에 대한 설명은 [변경 데이터 캡처&#40;SSIS&#41;](change-data-capture-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b1c-108">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="adding-the-data-flow-task"></a><span data-ttu-id="69b1c-109">데이터 흐름 태스크 추가</span><span class="sxs-lookup"><span data-stu-id="69b1c-109">Adding the Data Flow Task</span></span>  
 <span data-ttu-id="69b1c-110">패키지의 데이터 흐름에서 변경 데이터를 검색하고 발생한 변경 내용 유형을 기반으로 행을 구분한 다음 대상에 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-110">In the data flow of the package, you retrieve the change data, separate the rows based on the type of change that occurred, and then apply the changes to the destination.</span></span>  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a><span data-ttu-id="69b1c-111">패키지에 데이터 흐름 태스크를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="69b1c-111">To add a Data Flow task to the package</span></span>  
  
1.  <span data-ttu-id="69b1c-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **제어 흐름** 탭에서 데이터 흐름 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Control Flow** tab, add a Data Flow task.</span></span>  
  
2.  <span data-ttu-id="69b1c-113">쿼리 문자열을 준비한 이전 태스크를 데이터 흐름 태스크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-113">Connect the preceding task that prepared the query string to the Data Flow task.</span></span>  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a><span data-ttu-id="69b1c-114">변경 내용을 쿼리하도록 원본 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="69b1c-114">Configuring the Source Component to Query for Changes</span></span>  
 <span data-ttu-id="69b1c-115">원본 구성 요소는 변수에 준비되어 저장된 쿼리 문자열을 사용하여 변경된 데이터를 검색하는 테이블 반환 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-115">The source component uses the query string that was prepared and stored in a variable to calls the table-valued function that retrieves the changed data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69b1c-116">변수에 준비되어 저장된 쿼리 문자열에 대한 자세한 내용은 [변경 데이터에 대한 쿼리 준비](prepare-to-query-for-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b1c-116">For more information about the query string that was prepared and stored in a variable, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span> <span data-ttu-id="69b1c-117">변경 데이터를 검색하는 테이블 반환 함수에 대한 자세한 내용은 [변경 데이터 검색을 위한 함수 만들기](create-the-function-to-retrieve-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b1c-117">For more information about the table-valued function that retrieves the change data, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a><span data-ttu-id="69b1c-118">변경 데이터를 검색하도록 OLE DB 원본을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="69b1c-118">To configure an OLE DB source to retrieve the change data</span></span>  
  
1.  <span data-ttu-id="69b1c-119">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **데이터 흐름** 탭에서 OLE DB 원본을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Data Flow** tab, add an OLE DB source.</span></span>  
  
2.  <span data-ttu-id="69b1c-120">**OLE DB 원본 편집기**의 **연결 관리자** 페이지에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-120">In the **OLE DB Source Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="69b1c-121">원본 데이터베이스에 대한 올바른 연결을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-121">Configure a valid connection to the source database.</span></span>  
  
    2.  <span data-ttu-id="69b1c-122">**데이터 액세스 모드**에 **변수를 사용한 SQL 명령**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-122">For **Data access mode**, select **SQL command from variable**.</span></span>  
  
    3.  <span data-ttu-id="69b1c-123">**변수 이름**에 **User::SqlDataQuery**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-123">For **Variable name**, select **User::SqlDataQuery**.</span></span>  
  
3.  <span data-ttu-id="69b1c-124">**OLE DB 원본 편집기**의 **열** 페이지에서 원하는 모든 열이 출력 열에 매핑되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-124">In the **OLE DB Source Editor**, on the **Columns** page, make sure that all the columns that you want are mapped to output columns.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="69b1c-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="69b1c-125">Next Step</span></span>  
 <span data-ttu-id="69b1c-126">변경 데이터를 검색하도록 OLE DB 원본을 구성한 후 다음 단계는 패키지의 데이터 흐름 디자인을 시작하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="69b1c-126">After you have configured an OLE DB source to retrieve the change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="69b1c-127">**다음 항목:** [삽입, 업데이트 및 삭제 처리](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="69b1c-127">**Next topic:** [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>  
  
  
