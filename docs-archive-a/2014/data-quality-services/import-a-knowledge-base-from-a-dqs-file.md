---
title: .dqs 파일에서 기술 자료 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9b9786fe-9e80-429a-afcb-dc3b3dd6f0b0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 522c5f6d8f962cef77e215c21133927e8da4d04f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733203"
---
# <a name="import-a-knowledge-base-from-a-dqs-file"></a><span data-ttu-id="abd54-102">.dqs 파일에서 기술 자료 가져오기</span><span class="sxs-lookup"><span data-stu-id="abd54-102">Import a Knowledge Base from a .dqs File</span></span>
  <span data-ttu-id="abd54-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 .dqs 데이터 파일의 전체 기술 자료를 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-103">This topic describes how to import an entire knowledge base from a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="abd54-104">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션 내에서 기존 기술 자료를 내보내서 데이터 파일을 만듭니다([.dqs 파일로 기술 자료 내보내기](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="abd54-104">You create the data file by exporting an existing knowledge base from within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application (see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)).</span></span>  
  
 <span data-ttu-id="abd54-105">.dqs 데이터 파일을 사용하여 기술 자료의 내용을 내보낸 다음 동일한 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 또는 다른 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 에서 다른 기술 자료로 내용을 가져오면 기술 자료 생성 프로세스가 간소화되어 시간과 노력을 절감할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-105">Using a .dqs data file to export the contents of a knowledge base and then import the contents into another knowledge base on the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] or a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="abd54-106">기술 자료와 정보를 다른 사람과 공유하여 다른 사람의 시간을 절감할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-106">It enables you to share a knowledge base and its knowledge with others, saving them time.</span></span> <span data-ttu-id="abd54-107">.dqs 파일에는 연결된 참조 데이터 정보를 제외하고 도메인 및 일치 정책을 포함한 모든 기술 자료 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-107">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="abd54-108">게시된 데이터와 게시되지 않은 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-108">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="abd54-109">.dqs 데이터 파일은 암호화되어 있으므로 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-109">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="abd54-110">기술 자료를 가져올 때는 클라이언트 애플리케이션에 기술 자료 이름이 이미 있어 이름을 바꾸어야 하는 경우를 제외하고 동일한 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-110">When you import a knowledge base, you can use the same name, unless the knowledge base name already exists in the client application, in which case you must rename it.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="abd54-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="abd54-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="abd54-112">필수 조건</span><span class="sxs-lookup"><span data-stu-id="abd54-112">Prerequisites</span></span>  
 <span data-ttu-id="abd54-113">.dqs 파일에서 기술 자료를 가져오려면 기술 자료를 .dqs 파일로 이미 내보낸 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-113">To import a knowledge base from a .dqs file, you must have already exported the knowledge base into the .dqs file.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="abd54-114">보안</span><span class="sxs-lookup"><span data-stu-id="abd54-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="abd54-115">권한</span><span class="sxs-lookup"><span data-stu-id="abd54-115">Permissions</span></span>  
 <span data-ttu-id="abd54-116">.dqs 데이터 파일에서 기술 자료를 가져오려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-116">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a knowledge base from a .dqs data file.</span></span>  
  
##  <a name="import-a-knowledge-base-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="abd54-117">Dqs 파일에서 기술 자료 가져오기</span><span class="sxs-lookup"><span data-stu-id="abd54-117">Import a knowledge base from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="abd54-118">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-118">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="abd54-119">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **새 기술 자료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-119">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="abd54-120">기술 자료의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-120">Enter a name for the knowledge base.</span></span>  
  
4.  <span data-ttu-id="abd54-121">**기술 자료 만들기**에 대해 아래쪽 화살표를 클릭한 다음 **DQS 파일에서 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-121">Click the down arrow for **Create knowledge base from**, and then select **Import from DQS file**.</span></span>  
  
5.  <span data-ttu-id="abd54-122">**데이터 파일 선택**에서 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-122">For **Select data file**, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="abd54-123">**데이터 파일에서 가져오기** 대화 상자에서 가져올 .dqs 파일이 있는 폴더로 이동한 다음 파일의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-123">In the **Import from Data File** dialog box, move to the folder that contains the .dqs file that you want to import, and then click the name of the file.</span></span> <span data-ttu-id="abd54-124">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-124">Click **Open**.</span></span>  
  
7.  <span data-ttu-id="abd54-125">**도메인** 목록에 올바른 기술 자료와 도메인이 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-125">Verify that the correct knowledge base and domains are displayed in the **Domain** list.</span></span>  
  
8.  <span data-ttu-id="abd54-126">수행할 작업을 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-126">Select the activity that you want to perform, and then click **Create**.</span></span>  
  
9. <span data-ttu-id="abd54-127">**기술 자료 가져오기** 대화 상자에서 상태 줄에 가져오기가 완료되었다고 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-127">In the **Import Knowledge Base** dialog box, verify that the status line indicates that the import completed.</span></span> <span data-ttu-id="abd54-128">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-128">Click **OK**.</span></span>  
  
10. <span data-ttu-id="abd54-129">수행해야 하는 기술 자료 검색, 도메인 관리 또는 일치 정책 태스크를 완료한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-129">Complete the knowledge discovery, domain management, or matching policy tasks that you need to perform, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="abd54-130">**게시** 를 클릭하여 기술 자료의 정보를 게시하거나 **아니요** 를 클릭하여 게시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-130">Click **Publish** to publish the knowledge in the knowledge base, or **No** not to.</span></span>  
  
12. <span data-ttu-id="abd54-131">기술 자료를 게시한 경우 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-131">If you published the knowledge base, click **OK**.</span></span>  
  
13. <span data-ttu-id="abd54-132">Data Quality Services 홈 페이지에서 **최근 기술 자료**에 해당 기술 자료가 나열되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-132">In the Data Quality Services home page, verify that the knowledge base is listed under **Recent knowledge bases**.</span></span>  
  
##  <a name="follow-up-after-importing-a-knowledge-base-from-a-dqs-file"></a><a name="FollowUp"></a><span data-ttu-id="abd54-133">후속 작업: dqs 파일에서 기술 자료를 가져온 후</span><span class="sxs-lookup"><span data-stu-id="abd54-133">Follow Up: After Importing a Knowledge Base from a .dqs File</span></span>  
 <span data-ttu-id="abd54-134">.dqs 파일에서 기술 자료를 가져온 후 기술 자료에 정보를 추가하거나 기술 자료의 내용에 따라 정리 또는 일치 프로젝트에서 기술 자료를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd54-134">After you import a knowledge base from a .dqs file, you can add knowledge to the knowledge base or use the knowledge base in a cleansing or matching project, depending on the contents of the knowledge base.</span></span> <span data-ttu-id="abd54-135">자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md), [복합 도메인 관리](../../2014/data-quality-services/managing-a-composite-domain.md), [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md), [데이터 정리](../../2014/data-quality-services/data-cleansing.md) 또는 [데이터 일치](../../2014/data-quality-services/data-matching.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="abd54-135">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
