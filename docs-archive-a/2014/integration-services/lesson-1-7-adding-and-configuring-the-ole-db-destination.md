---
title: '7단계: OLE DB 대상 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da917ccc4ca756c2442e70477976b5a71f7eb56e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651122"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a><span data-ttu-id="e6ae2-102">7단계: OLE DB 대상 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="e6ae2-102">Step 7: Adding and Configuring the OLE DB Destination</span></span>
  <span data-ttu-id="e6ae2-103">이제 패키지는 플랫 파일 원본에서 데이터를 추출하여 대상과 호환되는 형식으로 이 데이터를 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-103">Your package now can extract data from the flat file source and transform that data into a format that is compatible with the destination.</span></span> <span data-ttu-id="e6ae2-104">다음 태스크에서는 변환된 데이터를 실제로 대상에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-104">The next task is to actually load the transformed data into the destination.</span></span> <span data-ttu-id="e6ae2-105">데이터를 로드하려면 데이터 흐름에 OLE DB 대상을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-105">To load the data, you must add an OLE DB destination to the data flow.</span></span> <span data-ttu-id="e6ae2-106">OLE DB 대상은 데이터베이스 테이블, 뷰 또는 SQL 명령을 사용하여 다양한 OLE DB 호환 데이터베이스에 데이터를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-106">The OLE DB destination can use a database table, view, or an SQL command to load data into a variety of OLE DB-compliant databases.</span></span>  
  
 <span data-ttu-id="e6ae2-107">이 절차에서는 OLE DB 대상을 추가하고 이전에 만든 OLE DB 연결 관리자를 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-107">In this procedure, you add and configure an OLE DB destination to use the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a><span data-ttu-id="e6ae2-108">예제 OLE DB 대상을 추가하고 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e6ae2-108">To add and configure the sample OLE DB destination</span></span>  
  
1.  <span data-ttu-id="e6ae2-109">**SSIS 도구 상자**에서 **기타 대상**을 확장 하 고 **OLE DB Destination** 을 **데이터 흐름** 탭의 디자인 화면으로 끌어다 놓습니다. OLE DB 대상을 **Lookup Date Key** 변환 바로 아래에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-109">In the **SSIS Toolbox**, expand **Other Destinations**, and drag **OLE DB Destination** onto the design surface of the **Data Flow** tab. Place the OLE DB destination directly below the **Lookup Date Key** transformation.</span></span>  
  
2.  <span data-ttu-id="e6ae2-110">**Lookup Date Key** 변환을 클릭하고 새로 추가한 **OLE DB 대상** 위로 녹색 화살표를 끌어 두 구성 요소를 함께 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-110">Click the **Lookup Date Key** transformation and drag the green arrow over to the newly added **OLE DB Destination** to connect the two components together.</span></span>  
  
3.  <span data-ttu-id="e6ae2-111">**입/출력 선택** 대화 상자에서 **출력** 목록 상자의 **조회 일치 항목 출력**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-111">In the **Input Output Selection** dialog box, in the **Output** list box, click **Lookup Match Output**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e6ae2-112">**데이터 흐름** 디자인 화면에서 새로 추가한 **OLE DB 대상** 구성 요소의 **OLE DB 대상** 을 클릭한 다음 이름을 **Sample OLE DB Destination**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-112">On the **Data Flow** design surface, click **OLE DB Destination** in the newly added **OLE DB Destination** component, and change the name to **Sample OLE DB Destination**.</span></span>  
  
5.  <span data-ttu-id="e6ae2-113">**Sample OLE DB Destination**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-113">Double-click **Sample OLE DB Destination**.</span></span>  
  
6.  <span data-ttu-id="e6ae2-114">**OLE DB 대상 편집기** 대화 상자의 **OLE DB 연결 관리자** 상자에서 **localhost.AdventureWorksDW2012** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-114">In the **OLE DB Destination Editor** dialog box, ensure that **localhost.AdventureWorksDW2012** is selected in the **OLE DB Connection manager** box.</span></span>  
  
7.  <span data-ttu-id="e6ae2-115">**테이블 또는 뷰 이름** 상자에서 **[dbo].[FactCurrencyRate]** 를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-115">In the **Name of the table or the view** box, type or select **[dbo].[FactCurrencyRate]**.</span></span>  
  
8.  <span data-ttu-id="e6ae2-116">새 테이블을 만들려면 **새로 만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-116">Click the **New** button to create a new table.</span></span>  <span data-ttu-id="e6ae2-117">스크립트에서 테이블의 이름을 변경하여 **NewFactCurrencyRate**를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-117">Change the name of the table in the script to read **NewFactCurrencyRate**.</span></span>  <span data-ttu-id="e6ae2-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="e6ae2-119">**확인**을 클릭하면 대화 상자가 닫히고 **테이블 또는 뷰 이름** 이 **NewFactCurrencyRate**로 자동으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-119">Upon clicking **OK**, the dialog will close and the **Name of the table or the view** will automatically change to **NewFactCurrencyRate**.</span></span>  
  
10. <span data-ttu-id="e6ae2-120">**매핑**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-120">Click **Mappings**.</span></span>  
  
11. <span data-ttu-id="e6ae2-121">**AverageRate**, **CurrencyKey**, **EndOfDayRate**및 **DateKey** 입력 열이 대상 열에 올바르게 매핑되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-121">Verify that the **AverageRate**, **CurrencyKey**, **EndOfDayRate**, and **DateKey** input columns are mapped correctly to the destination columns.</span></span> <span data-ttu-id="e6ae2-122">서로 같은 이름의 열이 매핑되어 있는 경우 매핑이 올바른 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-122">If same-named columns are mapped, the mapping is correct.</span></span>  
  
12. <span data-ttu-id="e6ae2-123">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-123">Click **OK**.</span></span>  
  
13. <span data-ttu-id="e6ae2-124">**Sample OLE DB Destination** 대상을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-124">Right-click the **Sample OLE DB Destination** destination and click **Properties**.</span></span>  
  
14. <span data-ttu-id="e6ae2-125">속성 창에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있고 `DefaultCodePage` 속성이 **1252**로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6ae2-125">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the`DefaultCodePage` property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e6ae2-126">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="e6ae2-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e6ae2-127">8단계: 1단원 패키지를 쉽게 이해할 수 있도록 만들기</span><span class="sxs-lookup"><span data-stu-id="e6ae2-127">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a><span data-ttu-id="e6ae2-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6ae2-128">See Also</span></span>  
 [<span data-ttu-id="e6ae2-129">OLE DB 대상</span><span class="sxs-lookup"><span data-stu-id="e6ae2-129">OLE DB Destination</span></span>](data-flow/ole-db-destination.md)  
  
  
