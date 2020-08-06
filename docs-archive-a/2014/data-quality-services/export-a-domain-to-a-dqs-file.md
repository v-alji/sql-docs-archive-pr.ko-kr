---
title: .dqs 파일로 도메인 내보내기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eba10d3d-b5c4-447b-8a30-fa07996cb28e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5d23e9efa2b3224aab5623201a54d1af56e49e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647851"
---
# <a name="export-a-domain-to-a-dqs-file"></a><span data-ttu-id="1f4f2-102">.dqs 파일로 도메인 내보내기</span><span class="sxs-lookup"><span data-stu-id="1f4f2-102">Export a Domain to a .dqs File</span></span>
  <span data-ttu-id="1f4f2-103">이 항목에는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 .dqs 파일로 도메인을 내보내는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-103">This topic describes how to export a domain to a .dqs file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="1f4f2-104">도메인 또는 전체 기술 자료를 데이터 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="1f4f2-105">기술 자료 내보내기에 대한 자세한 내용은 [.dqs 파일로 기술 자료 내보내기](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-105">For information about exporting a knowledge base, see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="1f4f2-106">한 기술 자료의 도메인을 .dqs 데이터 파일로 내보낸 다음 다른 기술 자료로 가져오면 기술 자료 생성 프로세스가 간소화되어 시간과 노력을 절감할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-106">Exporting a domain from one knowledge base to a .dqs data file, and then importing it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="1f4f2-107">도메인과 정보를 다른 사람과 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-107">It enables you to share a domain and its knowledge with others.</span></span>  
  
 <span data-ttu-id="1f4f2-108">단일 도메인 또는 복합 도메인을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-108">You can export either a single domain or composite domain.</span></span> <span data-ttu-id="1f4f2-109">단일 도메인을 포함하는 .dqs 파일에는 연결된 참조 데이터 정보를 제외하고 도메인 속성, 값 및 규칙을 비롯하여 모든 도메인 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules except for the attached reference data information.</span></span> <span data-ttu-id="1f4f2-110">복합 도메인을 포함하는 .dqs 파일에는 참조 데이터 정보를 제외하고 복합 도메인에 포함된 도메인에 대한 모든 도메인 데이터와 복합 도메인 속성, 관계 및 규칙을 비롯하여 모든 복합 도메인 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the domains that are contained in the composite domain, and the composite domain properties, relations, and rules, except for the reference data information.</span></span> <span data-ttu-id="1f4f2-111">필요한 경우 .dqs 파일을 가져온 후 도메인 또는 복합 도메인을 적절한 참조 데이터 서비스에 다시 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-111">You must attach the domain or the composite domain to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="1f4f2-112">게시된 데이터와 게시되지 않은 데이터를 모두 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-112">Both published and unpublished data is exported.</span></span>  
  
 <span data-ttu-id="1f4f2-113">내보내기 프로세스에서 만든 .dqs 데이터 파일은 암호화되므로 내용을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-113">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1f4f2-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1f4f2-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1f4f2-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="1f4f2-115">Prerequisites</span></span>  
 <span data-ttu-id="1f4f2-116">도메인을 .dqs 데이터 파일로 내보내려면 단일 도메인 또는 여러 개의 단일 도메인이 포함된 복합 도메인을 만들고 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-116">To export a domain to a .dqs data file, you must have created and selected a single domain or a composite domain containing multiple single domains.</span></span> <span data-ttu-id="1f4f2-117">기술 자료를 내보낼 .dqs 파일은 자동으로 생성되므로 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-117">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1f4f2-118">보안</span><span class="sxs-lookup"><span data-stu-id="1f4f2-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1f4f2-119">권한</span><span class="sxs-lookup"><span data-stu-id="1f4f2-119">Permissions</span></span>  
 <span data-ttu-id="1f4f2-120">도메인을 .dqs 데이터 파일로 내보내려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-120">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a domain to a .dqs data file.</span></span>  
  
##  <a name="export-a-domain-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="1f4f2-121">도메인을 dqs 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="1f4f2-121">Export a domain to a .dqs file</span></span>  
 <span data-ttu-id="1f4f2-122">모든 도메인 관리 페이지에서 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-122">You can export from any Domain Management page.</span></span> <span data-ttu-id="1f4f2-123">내보내기 명령은 사용자 인터페이스의 컨트롤과 도메인 목록 창의 상황에 맞는 메뉴에 있는 명령에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-123">The export command is available from both a control in the user interface and from a command in the context menu of the Domain List pane.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="1f4f2-124">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-124">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="1f4f2-125">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 도메인 관리 작업에서 기술 자료를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-125">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="1f4f2-126">**도메인 관리 페이지** (임의의 탭이 선택되어 있음)의 **도메인** 목록에서 단일 도메인 또는 복합 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-126">In the **Domain Management page** (with any tab selected), select a single domain or a composite domain in the **Domain** list.</span></span>  
  
4.  <span data-ttu-id="1f4f2-127">도메인 목록 위의 **기술 자료 데이터 내보내기** 아이콘을 클릭한 다음 **도메인 내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-127">Click the **Export Knowledge Base data** icon above the domain list, and then click **Export Domain**.</span></span> <span data-ttu-id="1f4f2-128">또는 **도메인** 목록에서 도메인을 마우스 오른쪽 단추를 클릭하고 **내보내기**를 가리킨 다음 **도메인 내보내기**를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-128">Alternatively, you can right-click the domain in the **Domain** list, point to **Export**, and then click **Export Domain**.</span></span>  
  
5.  <span data-ttu-id="1f4f2-129">**데이터 파일로 내보내기** 대화 상자에서 파일을 저장할 폴더로 이동하여 파일의 이름을 지정하거나 기본 이름을 유지한 후 **다른 이름으로 저장** 형식으로 **DQS 데이터 파일(\*.dqs)** 을 지정하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-129">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the default name, keep **DQS Data Files (\*.dqs)** as the **Save as type**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="1f4f2-130">**도메인 내보내기** 대화 상자에서 상태 줄에 내보내기가 완료되었다고 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-130">In the **Export Domain** dialog box, verify that the status line in the dialog box indicates that the export completed.</span></span> <span data-ttu-id="1f4f2-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-131">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a><span data-ttu-id="1f4f2-132">후속 작업: 도메인을 dqs 파일로 내보낸 후</span><span class="sxs-lookup"><span data-stu-id="1f4f2-132">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="1f4f2-133">도메인을 .dqs 파일로 내보낸 후 다른 기술 자료로 해당 도메인을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f4f2-133">After you export a domain to a .dqs file, you can import the domain into another knowledge base.</span></span>  
  
  
