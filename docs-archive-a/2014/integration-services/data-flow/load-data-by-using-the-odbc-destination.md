---
title: ODBC 대상을 사용하여 데이터 로드 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 339ec0a8-922e-48c0-97b3-fc5ee34f95e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8bf0b30619c2886df6ddb28858cf98bad858421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731939"
---
# <a name="load-data-by-using-the-odbc-destination"></a><span data-ttu-id="80dcb-102">ODBC 대상을 사용하여 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="80dcb-102">Load Data by Using the ODBC Destination</span></span>
  <span data-ttu-id="80dcb-103">이 절차에서는 ODBC 대상을 사용하여 데이터를 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-103">This procedure shows how to load data by using the ODBC destination.</span></span> <span data-ttu-id="80dcb-104">ODBC 대상을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-104">To add and configure an ODBC destination, the package must already include at least one Data Flow task and source.</span></span>  
  
### <a name="to-load-data-using-an-odbc-destination"></a><span data-ttu-id="80dcb-105">ODBC 대상을 사용하여 데이터를 로드하려면</span><span class="sxs-lookup"><span data-stu-id="80dcb-105">To load data using an ODBC destination</span></span>  
  
1.  <span data-ttu-id="80dcb-106">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 원하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="80dcb-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 ODBC 대상을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC destination to the design surface.</span></span>  
  
3.  <span data-ttu-id="80dcb-108">데이터 흐름 구성 요소의 사용 가능한 출력을 ODBC 대상의 입력으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-108">Drag an available output of a data flow component to the input of the ODBC destination.</span></span>  
  
4.  <span data-ttu-id="80dcb-109">ODBC 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-109">Double-click the ODBC destination.</span></span>  
  
5.  <span data-ttu-id="80dcb-110">**ODBC 대상 편집기** 대화 상자의 **연결 관리자** 페이지에서 기존 ODBC 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-110">In the **ODBC Destination Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
6.  <span data-ttu-id="80dcb-111">데이터 액세스 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-111">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="80dcb-112">**테이블 이름 - 일괄 처리**: 일괄 처리 모드에서 작업하도록 ODBC 대상을 구성하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-112">**Table Name - Batch**: Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="80dcb-113">이 옵션을 선택하면 **일괄 처리 크기**를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-113">When you select this option, you can set the **Batch size**.</span></span>  
  
    -   <span data-ttu-id="80dcb-114">**테이블 이름 - 행 단위**: 각 행을 한 번에 하나씩 대상 테이블에 삽입하도록 ODBC 대상을 구성하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-114">**Table Name - Row by Row**: Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="80dcb-115">이 옵션을 선택하면 데이터가 한 번에 한 행씩 테이블로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-115">When you select this option, the data is loaded into the table one row at a time.</span></span>  
  
7.  <span data-ttu-id="80dcb-116">**테이블 또는 뷰 이름** 필드의 목록에서 데이터베이스의 가용 테이블 또는 뷰를 선택하거나 테이블을 식별하는 정규식을 입력합니다. 이 목록에는 처음 1000개의 테이블만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-116">In the **Name of the table or the view** field, select an available table or view from the database from the list or type in a regular expression to identify the table.This list contains the first 1000 tables only.</span></span> <span data-ttu-id="80dcb-117">데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(\*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-117">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
8.  <span data-ttu-id="80dcb-118">**미리 보기** 를 클릭하여 ODBC 대상에서 선택한 테이블의 데이터 행을 200개까지 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-118">You can click **Preview** to view up to 200 rows of the data from the table selected in the ODBC destination.</span></span>  
  
9. <span data-ttu-id="80dcb-119">**매핑** 을 클릭한 후 **사용 가능한 입력 열** 목록의 열을 **사용 가능한 대상 열** 목록의 열로 끌어서 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-119">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
10. <span data-ttu-id="80dcb-120">오류 출력을 구성하려면 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-120">To configure the error output, click **Error Output**.</span></span>  
  
11. <span data-ttu-id="80dcb-121">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="80dcb-122">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80dcb-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80dcb-123">See Also</span></span>  
 <span data-ttu-id="80dcb-124">[ODBC 대상 편집기&#40;연결 관리자 페이지&#41;](../odbc-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="80dcb-124">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="80dcb-125">[ODBC 대상 편집기&#40;매핑 페이지&#41;](../odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="80dcb-125">[ODBC Destination Editor &#40;Mappings Page&#41;](../odbc-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="80dcb-126">ODBC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="80dcb-126">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
  
