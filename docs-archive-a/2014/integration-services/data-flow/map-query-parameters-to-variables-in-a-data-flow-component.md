---
title: 쿼리 매개 변수를 데이터 흐름 구성 요소의 변수에 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b38940313397c7be7a8bcdbd2bf7f5233583096e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741148"
---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a><span data-ttu-id="ddefa-102">쿼리 매개 변수를 데이터 흐름 구성 요소의 변수에 매핑</span><span class="sxs-lookup"><span data-stu-id="ddefa-102">Map Query Parameters to Variables in a Data Flow Component</span></span>
  <span data-ttu-id="ddefa-103">매개 변수가 있는 쿼리를 사용하도록 OLE DB 원본을 구성할 경우 매개 변수를 변수에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-103">When you configure the OLE DB source to use parameterized queries, you can map the parameters to variables.</span></span>  
  
 <span data-ttu-id="ddefa-104">OLE DB 원본은 데이터 원본에 연결될 때 매개 변수가 있는 쿼리를 사용하여 데이터를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-104">The OLE DB source uses parameterized queries to filter data when the source connects to a data source.</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="ddefa-105">쿼리 매개 변수를 변수에 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="ddefa-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="ddefa-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="ddefa-107">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="ddefa-108">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 OLE DB 원본을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="ddefa-109">OLE DB 원본을 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-109">Right-click the OLE DB source, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="ddefa-110">**OLE DB 원본 편집기**에서 데이터 원본에 연결하는 데 사용할 OLE DB 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 OLE DB 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-110">In the **OLE DB Source Editor**, select an OLE DB connection manager to use to connect to the data source, or click **New** to create a new OLE DB connection manager.</span></span>  
  
6.  <span data-ttu-id="ddefa-111">데이터 액세스 모드에 대해 **SQL 명령** 옵션을 선택한 다음 **SQL 명령 텍스트** 창에 매개 변수가 있는 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-111">Select the **SQL command** option for data access mode, and then type a parameterized query in the **SQL command text** pane.</span></span>  
  
7.  <span data-ttu-id="ddefa-112">**매개 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-112">Click **Parameters**.</span></span>  
  
8.  <span data-ttu-id="ddefa-113">**쿼리 매개 변수 설정** 대화 상자에서 **매개 변수** 목록의 각 매개 변수를 **변수** 목록의 변수에 매핑하거나 **\<New variable>** 를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-113">In the **Set Query Parameters** dialog box, map each parameter in the **Parameters** list to a variable in the **Variables** list, or create a new variable by clicking **\<New variable>**.</span></span> <span data-ttu-id="ddefa-114">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ddefa-115">패키지, Foreach 루프와 같은 부모 컨테이너 또는 데이터 흐름 구성 요소가 포함된 데이터 흐름 태스크의 범위에 속하는 사용자 정의 변수와 시스템 변수만 매핑에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-115">Only system variables and user-defined variables that are in the scope of the package, a parent container such as a Foreach Loop, or the Data Flow task that contains the data flow component are available for mapping.</span></span> <span data-ttu-id="ddefa-116">변수는 매개 변수가 할당된 WHERE 절의 열과 호환되는 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-116">The variable must have a data type that is compatible with the column in the WHERE clause to which the parameter is assigned.</span></span>  
  
9. <span data-ttu-id="ddefa-117">**미리 보기** 를 클릭하면 쿼리에서 반환되는 데이터 행을 최대 200개까지 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-117">You can click **Preview** to view up to 200 rows of the data that the query returns.</span></span>  
  
10. <span data-ttu-id="ddefa-118">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddefa-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddefa-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddefa-119">See Also</span></span>  
 <span data-ttu-id="ddefa-120">[OLE DB 원본](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="ddefa-120">[OLE DB Source](ole-db-source.md) </span></span>  
 [<span data-ttu-id="ddefa-121">조회 변환</span><span class="sxs-lookup"><span data-stu-id="ddefa-121">Lookup Transformation</span></span>](transformations/lookup-transformation.md)  
  
  
