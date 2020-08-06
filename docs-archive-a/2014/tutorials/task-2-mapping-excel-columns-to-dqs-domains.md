---
title: '태스크 2: Excel 열을 DQS 도메인에 매핑 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 293b035ff52845959e2c8b70c63df643ae6e3e55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659754"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a><span data-ttu-id="812ff-102">태스크 2: Excel 열을 DQS 도메인으로 매핑</span><span class="sxs-lookup"><span data-stu-id="812ff-102">Task 2: Mapping Excel Columns to DQS Domains</span></span>
    
1.  <span data-ttu-id="812ff-103">**맵** 페이지에서 **데이터 원본** 에 대해 **Excel 파일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-103">In the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
2.  <span data-ttu-id="812ff-104">**찾아보기**를 클릭 하 고 **Suppliers.xlsx**를 선택한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-104">Click **Browse**, select **Suppliers.xlsx**, and click **Open**.</span></span>  
  
3.  <span data-ttu-id="812ff-105">**워크시트**에 대해 **IncomingSuppliers $** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-105">Select **IncomingSuppliers$** for the **Worksheet**.</span></span>  
  
4.  <span data-ttu-id="812ff-106">다음 표 및 스크린 샷에 표시된 대로 열을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-106">Map columns as shown in the following table and screenshot.</span></span> <span data-ttu-id="812ff-107">**상태** 도메인에 대 한 매핑을 만들 때 목록 바로 위에 있는 도구 모음에서 **열 매핑 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-107">When creating mappings for the **State** domain, click **Add a column mapping** button on the toolbar located just above the list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="812ff-108">정리에 **공급자 ID** 열/도메인을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-108">You are not using **Supplier ID** column/domain for cleansing.</span></span> <span data-ttu-id="812ff-109">나중에 일치 작업에서 **공급자 ID** 도메인을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-109">You will use the **Supplier ID** domain later in the matching activity.</span></span>  
  
    |<span data-ttu-id="812ff-110">Excel 열</span><span class="sxs-lookup"><span data-stu-id="812ff-110">Excel column</span></span>|<span data-ttu-id="812ff-111">DQS 도메인</span><span class="sxs-lookup"><span data-stu-id="812ff-111">DQS Domain</span></span>|  
    |------------------|----------------|  
    |<span data-ttu-id="812ff-112">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="812ff-112">Supplier Name</span></span>|<span data-ttu-id="812ff-113">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="812ff-113">Supplier Name</span></span>|  
    |<span data-ttu-id="812ff-114">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="812ff-114">ContactEmailAddress</span></span>|<span data-ttu-id="812ff-115">담당자 이메일</span><span class="sxs-lookup"><span data-stu-id="812ff-115">Contact Email</span></span>|  
    |<span data-ttu-id="812ff-116">Address Line</span><span class="sxs-lookup"><span data-stu-id="812ff-116">Address Line</span></span>|<span data-ttu-id="812ff-117">Address Line</span><span class="sxs-lookup"><span data-stu-id="812ff-117">Address Line</span></span>|  
    |<span data-ttu-id="812ff-118">도시</span><span class="sxs-lookup"><span data-stu-id="812ff-118">City</span></span>|<span data-ttu-id="812ff-119">도시</span><span class="sxs-lookup"><span data-stu-id="812ff-119">City</span></span>|  
    |<span data-ttu-id="812ff-120">주</span><span class="sxs-lookup"><span data-stu-id="812ff-120">State</span></span>|<span data-ttu-id="812ff-121">주</span><span class="sxs-lookup"><span data-stu-id="812ff-121">State</span></span>|  
    |<span data-ttu-id="812ff-122">Country ( **+ (열 매핑 추가)** 도구 모음을 클릭 하 여 행 추가)</span><span class="sxs-lookup"><span data-stu-id="812ff-122">Country (Click **+(Add a column mapping)** toolbar to add a row)</span></span>|<span data-ttu-id="812ff-123">국가</span><span class="sxs-lookup"><span data-stu-id="812ff-123">Country</span></span>|  
    |<span data-ttu-id="812ff-124">Zip Code</span><span class="sxs-lookup"><span data-stu-id="812ff-124">Zip Code</span></span>|<span data-ttu-id="812ff-125">Zip</span><span class="sxs-lookup"><span data-stu-id="812ff-125">Zip</span></span>|  
  
     <span data-ttu-id="812ff-126">![Excel 열에서 도메인으로 매핑](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Excel 열에서 도메인으로 매핑")</span><span class="sxs-lookup"><span data-stu-id="812ff-126">![Mappings of Excel Columns to Domains](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Mappings of Excel Columns to Domains")</span></span>  
  
5.  <span data-ttu-id="812ff-127">**주소 유효성 검사** 복합 도메인 내의 개별 도메인을 모두 매핑한 경우 복합 도메인은 정리 프로세스에 자동으로 참여 합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-127">As you have mapped all the individual domains within the **Address Validation** composite domain, the composite domain automatically participates in the cleansing process.</span></span> <span data-ttu-id="812ff-128">**복합 도메인 보기/선택** 단추를 클릭 하 여 **주소 유효성 검사** 복합 도메인이 자동으로 선택 되어 있는지 확인 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-128">Click **View/Select Composite Domains** button to see that the **Address Validation** composite domain is automatically selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="812ff-129">![복합 도메인 보기/선택 대화 상자](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "복합 도메인 보기/선택 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="812ff-129">![View/Select Composite Domains Dialog Box](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "View/Select Composite Domains Dialog Box")</span></span>  
  
6.  <span data-ttu-id="812ff-130">**다음** 을 클릭 하 여 **정리** 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="812ff-130">Click **Next** to switch to the **Cleanse** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="812ff-131">다음 단계</span><span class="sxs-lookup"><span data-stu-id="812ff-131">Next Step</span></span>  
 [<span data-ttu-id="812ff-132">태스크 3: 공급자 기술 자료에 대한 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="812ff-132">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
