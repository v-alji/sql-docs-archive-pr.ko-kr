---
title: 복합 도메인의 값 관계 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 135934ec99fed612609e5e1b962f08bb93b98ede
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742587"
---
# <a name="use-value-relations-in-a-composite-domain"></a><span data-ttu-id="f320e-102">복합 도메인의 값 관계 사용</span><span class="sxs-lookup"><span data-stu-id="f320e-102">Use Value Relations in a Composite Domain</span></span>
  <span data-ttu-id="f320e-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 기술 자료 검색 프로세스 중에 복합 도메인에 대해 발견된 값 조합을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-103">This topic describes how to view value combinations found for the composite domain during the knowledge discovery process in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="f320e-104">이 페이지에서는 값 조합의 발생 횟수를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-104">This page shows the number of occurrences of the value combinations.</span></span> <span data-ttu-id="f320e-105">복합 도메인에는 값 관리가 지원되지 않으므로 이러한 값에 대해 어떠한 작업도 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-105">Value management is not supported for composite domains, so you cannot perform any operations on these values.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f320e-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f320e-106">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f320e-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="f320e-107">Prerequisites</span></span>  
 <span data-ttu-id="f320e-108">값 관계를 보려면 복합 도메인을 만들고 열어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-108">To view value relations, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f320e-109">보안</span><span class="sxs-lookup"><span data-stu-id="f320e-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f320e-110">권한</span><span class="sxs-lookup"><span data-stu-id="f320e-110">Permissions</span></span>  
 <span data-ttu-id="f320e-111">복합 도메인의 값 관계를 보려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to view value relations in a composite domain.</span></span>  
  
##  <a name="view-value-relations"></a><a name="Use"></a><span data-ttu-id="f320e-112">값 관계 보기</span><span class="sxs-lookup"><span data-stu-id="f320e-112">View Value Relations</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="f320e-113">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="f320e-114">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 기술 자료를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="f320e-115">**도메인 관리** 를 작업으로 선택한 다음 **열기** 또는 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-115">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="f320e-116">자세한 내용은 [기술 자료 만들기](../../2014/data-quality-services/create-a-knowledge-base.md) 또는 [기술 자료 열기](../../2014/data-quality-services/open-a-knowledge-base.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f320e-116">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="f320e-117">**도메인 관리** 페이지의 **도메인 목록** 에서 도메인 규칙을 만들 복합 도메인을 선택하거나 새 복합 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-117">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="f320e-118">새 도메인을 만들어야 하는 경우 [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f320e-118">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="f320e-119">**값 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-119">Click the **Value Relations** tab.</span></span>  
  
5.  <span data-ttu-id="f320e-120">각 값 조합에 대해 표시되는 빈도를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-120">View the frequencies displayed for each value combination.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f320e-121">**값** 테이블에서는 복합 도메인에 있는 각각의 값 조합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-121">The **Value** table shows each combination of values that exists in the composite domain.</span></span> <span data-ttu-id="f320e-122">각 값은 값이 적용되는 단일 도메인에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-122">Each value is shown in the single domain that it applies to.</span></span> <span data-ttu-id="f320e-123">값 관계 테이블은 기본적으로 빈도순으로 정렬되지만 다른 열을 클릭하여 해당 열을 기준으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-123">The default sorting of the value relations table is by frequency, but you can click on another column to sort by that column.</span></span> <span data-ttu-id="f320e-124">빈도가 20보다 크거나 같은 해당 값만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-124">Only those values with a frequency greater than or equal to 20 are displayed.</span></span>  
  
6.  <span data-ttu-id="f320e-125">테이블의 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-125">You cannot change any of the values in the table.</span></span> <span data-ttu-id="f320e-126">다른 작업을 수행한 경우 **마침** 을 클릭하여 도메인 관리 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-126">If you have performed other operations, click **Finish** to complete the domain management activity.</span></span> <span data-ttu-id="f320e-127">그렇지 않으면 **취소**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-127">Otherwise, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-viewing-value-relations"></a><a name="FollowUp"></a><span data-ttu-id="f320e-128">후속 작업: 값 관계를 본 후</span><span class="sxs-lookup"><span data-stu-id="f320e-128">Follow Up: After Viewing Value Relations</span></span>  
 <span data-ttu-id="f320e-129">값 관계를 본 후 도메인에 대해 다른 도메인 관리 태스크를 수행하거나, 기술 자료 검색을 수행하여 도메인에 정보를 추가하거나, 도메인에 일치 정책을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f320e-129">After you view value relations, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="f320e-130">자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md) 또는 [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f320e-130">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
