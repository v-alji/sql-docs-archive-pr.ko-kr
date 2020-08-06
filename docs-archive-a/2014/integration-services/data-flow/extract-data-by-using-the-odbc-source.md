---
title: ODBC 원본을 사용하여 데이터 추출 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c05efe2b0479047280fc093ee555e037c77d82e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742432"
---
# <a name="extract-data-by-using-the-odbc-source"></a><span data-ttu-id="b3cd5-102">ODBC 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="b3cd5-102">Extract Data by Using the ODBC Source</span></span>
  <span data-ttu-id="b3cd5-103">이 절차에서는 ODBC 원본을 사용하여 데이터를 추출하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-103">This procedure describes how to extract data by using an ODBC source.</span></span> <span data-ttu-id="b3cd5-104">ODBC 원본을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크가 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-104">To add and configure an ODBC source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-odbc-source"></a><span data-ttu-id="b3cd5-105">ODBC 원본을 사용하여 데이터를 추출하려면</span><span class="sxs-lookup"><span data-stu-id="b3cd5-105">To extract data using an ODBC source</span></span>  
  
1.  <span data-ttu-id="b3cd5-106">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 원하는 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="b3cd5-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 ODBC 원본을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC source to the design surface.</span></span>  
  
3.  <span data-ttu-id="b3cd5-108">ODBC 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-108">Double-click the ODBC source.</span></span>  
  
4.  <span data-ttu-id="b3cd5-109">**ODBC 원본 편집기** 대화 상자의 **연결 관리자** 페이지에서 기존 ODBC 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-109">In the **ODBC Source Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="b3cd5-110">데이터 액세스 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-110">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="b3cd5-111">**테이블 이름**: 데이터베이스의 테이블 또는 뷰를 선택하거나 ODBC 연결 관리자가 연결될 테이블을 식별하는 정규식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-111">**Table Name**: Select a table or view in the database or type a regular expression to identify the table to which the ODBC connection manager connects.</span></span>  
  
         <span data-ttu-id="b3cd5-112">이 목록에는 처음 1000개의 테이블만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-112">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="b3cd5-113">데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(\*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-113">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
    -   <span data-ttu-id="b3cd5-114">**SQL 명령**: SQL 명령을 입력하거나 **찾아보기** 를 클릭하여 텍스트 파일에서 SQL 쿼리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-114">**SQL Command**: Type an SQL Command or click **Browse** to load the SQL query from a text file.</span></span>  
  
6.  <span data-ttu-id="b3cd5-115">**미리 보기** 를 클릭하면 ODBC 원본에 의해 추출된 최대 200개의 데이터 행을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-115">You can click **Preview** to view up to 200 rows of the data extracted by the ODBC source.</span></span>  
  
7.  <span data-ttu-id="b3cd5-116">외부 및 출력 열 사이의 매핑을 업데이트하려면 **열** 을 클릭하고 **외부 열** 목록에서 다른 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-116">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="b3cd5-117">필요에 따라 **출력 열** 목록에서 값을 편집하여 출력 열의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-117">If necessary, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="b3cd5-118">오류 출력을 구성하려면 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-118">To configure the error output, click **Error Output**.</span></span>  
  
10. <span data-ttu-id="b3cd5-119">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-119">Click **OK**.</span></span>  
  
11. <span data-ttu-id="b3cd5-120">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cd5-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3cd5-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3cd5-121">See Also</span></span>  
 <span data-ttu-id="b3cd5-122">[ODBC 원본 편집기&#40;연결 관리자 페이지&#41;](../odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="b3cd5-122">[ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="b3cd5-123">[ODBC 원본 편집기&#40;열 페이지&#41;](../odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="b3cd5-123">[ODBC Source Editor &#40;Columns Page&#41;](../odbc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="b3cd5-124">ODBC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b3cd5-124">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
  
