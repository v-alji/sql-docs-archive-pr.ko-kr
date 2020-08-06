---
title: .dqs 파일에서 도메인 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fabd88b0-22b3-4543-a993-6d5b202ded80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2e08837fd0b160732b506af77a6cf4a1cbe1966f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732048"
---
# <a name="import-a-domain-from-a-dqs-file"></a><span data-ttu-id="250fa-102">.dqs 파일에서 도메인 가져오기</span><span class="sxs-lookup"><span data-stu-id="250fa-102">Import a Domain from a .dqs File</span></span>
  <span data-ttu-id="250fa-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 .dqs 파일의 도메인을 기존 기술 자료로 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-103">This topic describes how to import a domain from a .dqs file into an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="250fa-104">.dqs 데이터 파일은 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션에서 도메인이나 기술 자료를 내보내면 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-104">A .dqs data file is created by exporting a domain or knowledge base from the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="250fa-105">.dqs 데이터 파일은 암호화되어 있으므로 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-105">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="250fa-106">.dqs 데이터 파일을 사용하여 한 기술 자료의 도메인을 내보낸 다음 다른 기술 자료로 가져오면 기술 자료 생성 프로세스가 간소화되어 시간과 노력을 절감할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-106">Using a .dqs data file to export a domain from one knowledge base and then import it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="250fa-107">도메인과 정보를 다른 사람과 공유하여 다른 사람의 시간을 절감할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-107">It enables you to share a domain and its knowledge with others, saving them time.</span></span> <span data-ttu-id="250fa-108">단일 도메인 하나 또는 복합 도메인 하나(여러 단일 도메인 포함)를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-108">You can import either one single domain or one composite domain (containing multiple single domains).</span></span> <span data-ttu-id="250fa-109">단일 도메인을 포함하는 .dqs 파일에는 매핑된 참조 데이터 정보를 제외하고 도메인 속성, 값 및 규칙 데이터를 비롯하여 모든 도메인 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules data, except for the mapped reference data information.</span></span> <span data-ttu-id="250fa-110">복합 도메인을 포함하는 .dqs 파일에는 매핑된 참조 데이터를 제외하고 복합 도메인에 포함된 단일 도메인에 대한 모든 도메인 데이터와 복합 도메인 속성, 값 관계 및 CD 규칙을 비롯하여 모든 복합 도메인 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the singles domains that are contained within the composite domain, and the composite domain properties, value relations, and CD rules, except for the mapped reference data.</span></span> <span data-ttu-id="250fa-111">게시된 데이터와 게시되지 않은 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-111">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="250fa-112">도메인을 가져올 때 도메인 이름은 원래 내보내진 도메인의 이름과 동일하게 유지됩니다. 단, 도메인 이름이 이미 있는 경우에는 DQS에서 이름에 "_1"을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-112">When you import a domain, the name of the domain remains the same as the name of the domain that was originally exported, unless the domain name already exists, in which case DQS will append "_1" to the name.</span></span> <span data-ttu-id="250fa-113">또한 기존 도메인과 동일한 이름을 가진 개별 도메인이 포함된 복합 도메인을 가져오는 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-113">This is also true if you import a composite domain that contains an individual domain with the same name as an existing domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="250fa-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="250fa-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="250fa-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="250fa-115">Prerequisites</span></span>  
 <span data-ttu-id="250fa-116">.dqs 파일에서 도메인을 가져오려면 단일 도메인 하나 또는 복합 도메인 하나(여러 단일 도메인 포함)를 .dqs 파일로 이미 내보낸 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-116">To import a domain from a .dqs file, you must have already exported one single domain or one composite domain (containing multiple single domains) into the .dqs file.</span></span> <span data-ttu-id="250fa-117">.dqs 파일에는 도메인이 하나만 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-117">The .dqs file must only contain one domain.</span></span> <span data-ttu-id="250fa-118">또한 도메인을 가져올 기술 자료를 만들고 열어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-118">You must also have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="250fa-119">보안</span><span class="sxs-lookup"><span data-stu-id="250fa-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="250fa-120">권한</span><span class="sxs-lookup"><span data-stu-id="250fa-120">Permissions</span></span>  
 <span data-ttu-id="250fa-121">.dqs 데이터 파일에서 도메인을 가져오려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-121">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a domain from a .dqs data file.</span></span>  
  
##  <a name="import-a-domain-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="250fa-122">Dqs 파일에서 도메인 가져오기</span><span class="sxs-lookup"><span data-stu-id="250fa-122">Import a domain from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="250fa-123">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-123">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="250fa-124">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 도메인 관리 작업에서 기술 자료를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="250fa-125">**데이터 파일에서 도메인 가져오기** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-125">Click the **Import Domain from data file** icon.</span></span>  
  
4.  <span data-ttu-id="250fa-126">**데이터 파일에서 가져오기** 대화 상자에서 가져올 파일이 있는 폴더로 이동하고 파일을 선택한 다음(DQS 파일 형식) **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-126">In the **Import from Data File** dialog box, move to the folder that you want to import the file from, select the file (of type DQS File), and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="250fa-127">**도메인 가져오기** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-127">In the **Import Domain** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="250fa-128">도메인을 가져올 .dqs 파일에 단일 도메인 또는 복합 도메인(여러 단일 도메인 포함)이 하나만 포함된 경우에만 가져오기 작업이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-128">The import operation will succeed only if the .dqs file that you are importing from contains only one single domain or one composite domain (containing multiple single domains).</span></span>  
  
6.  <span data-ttu-id="250fa-129">가져온 도메인이 **도메인** 목록에 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-129">Verify that the domain that you imported is displayed in the **Domain** list.</span></span> <span data-ttu-id="250fa-130">복합 도메인을 가져온 경우 복합 도메인과 포함된 단일 도메인이 모두 **도메인** 목록에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-130">If you imported a composite domain, verify that the composite domain and the single domains contained in it are all in the **Domain** list.</span></span>  
  
##  <a name="follow-up-after-importing-a-domain-from-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="250fa-131">후속 작업: .dqs 파일에서 도메인을 가져온 후</span><span class="sxs-lookup"><span data-stu-id="250fa-131">Follow Up: After Importing a Domain from a .dqs File</span></span>  
 <span data-ttu-id="250fa-132">.dqs 파일에서 도메인을 가져온 후 도메인에 정보를 추가하거나 도메인의 내용에 따라 정리 또는 일치 프로젝트에서 도메인을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="250fa-132">After you import a domain from a .dqs file, you can add knowledge to the domain or use the domain in a cleansing or matching project, depending on the contents of the domain.</span></span> <span data-ttu-id="250fa-133">자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md), [복합 도메인 관리](../../2014/data-quality-services/managing-a-composite-domain.md), [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md), [데이터 정리](../../2014/data-quality-services/data-cleansing.md) 또는 [데이터 일치](../../2014/data-quality-services/data-matching.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="250fa-133">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
