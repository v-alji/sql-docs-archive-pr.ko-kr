---
title: OLE DB 원본을 사용하여 데이터 추출 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 352d62cc66e3f17fb10839086e7ee9c5307f1a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742431"
---
# <a name="extract-data-by-using-the-ole-db-source"></a><span data-ttu-id="99704-102">OLE DB 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="99704-102">Extract Data by Using the OLE DB Source</span></span>
  <span data-ttu-id="99704-103">OLE DB 원본을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크가 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-103">To add and configure an OLE DB source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-ole-db-source"></a><span data-ttu-id="99704-104">OLE DB 원본을 사용하여 데이터를 추출하려면</span><span class="sxs-lookup"><span data-stu-id="99704-104">To extract data using an OLE DB Source</span></span>  
  
1.  <span data-ttu-id="99704-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="99704-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="99704-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="99704-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="99704-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 OLE DB 원본을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="99704-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="99704-108">OLE DB 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-108">Double-click the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="99704-109">**OLE DB 원본 편집기** 대화 상자의 **연결 관리자** 페이지에서 기존 OLE DB 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99704-109">In the **OLE DB Source Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="99704-110">자세한 내용은 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99704-110">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
6.  <span data-ttu-id="99704-111">다음과 같은 데이터 액세스 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-111">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="99704-112">**테이블 또는 뷰** OLE DB 연결 관리자에서 연결할 데이터베이스의 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-112">**Table or view** Select a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="99704-113">**테이블 이름 또는 뷰 이름 변수** OLE DB 연결 관리자에서 연결할 데이터베이스의 테이블 또는 뷰의 이름이 포함된 사용자 정의 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-113">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="99704-114">**SQL 명령** SQL 명령을 입력하거나 **쿼리 작성** 을 클릭하여 **쿼리 작성기**를 사용하여 SQL 명령을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-114">**SQL command** Type an SQL command or click **Build Query** to write an SQL command using the **Query Builder**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="99704-115">명령에는 매개 변수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99704-115">The command can include parameters.</span></span> <span data-ttu-id="99704-116">자세한 내용은 [쿼리 매개 변수를 데이터 흐름 구성 요소의 변수에 매핑](map-query-parameters-to-variables-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99704-116">For more information, see [Map Query Parameters to Variables in a Data Flow Component](map-query-parameters-to-variables-in-a-data-flow-component.md).</span></span>  
  
    -   <span data-ttu-id="99704-117">**변수를 사용한 SQL 명령** SQL 명령이 포함된 사용자 정의 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-117">**SQL command from variable** Select the user-defined variable that contains the SQL command.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="99704-118">OLE DB 원본이 포함된 동일 데이터 흐름 태스크의 범위나 동일 패키지 범위에 변수가 정의되어 있어야 하며, 변수에는 문자열 데이터 형식이 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-118">The variables must be defined in the scope of the same Data Flow task that contains the OLE DB source, or in the scope of the same package; additionally, the variable must have a string data type.</span></span>  
  
7.  <span data-ttu-id="99704-119">외부 및 출력 열 사이의 매핑을 업데이트하려면 **열** 을 클릭하고 **외부 열** 목록에서 다른 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-119">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="99704-120">필요에 따라 **출력 열** 목록에서 값을 편집하여 출력 열의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-120">Optionally, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="99704-121">오류 출력을 구성하려면 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-121">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="99704-122">자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99704-122">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="99704-123">**미리 보기** 를 클릭하면 OLE DB 원본에서 추출된 최대 200개의 데이터 행을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99704-123">You can click **Preview** to view up to 200 rows of the data extracted by the OLE DB source.</span></span>  
  
11. <span data-ttu-id="99704-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-124">Click **OK**.</span></span>  
  
12. <span data-ttu-id="99704-125">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99704-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99704-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99704-126">See Also</span></span>  
 <span data-ttu-id="99704-127">[OLE DB 원본](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="99704-127">[OLE DB Source](ole-db-source.md) </span></span>  
 <span data-ttu-id="99704-128">[Integration Services 변환](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="99704-128">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="99704-129">[Integration Services 경로](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="99704-129">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="99704-130">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="99704-130">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
