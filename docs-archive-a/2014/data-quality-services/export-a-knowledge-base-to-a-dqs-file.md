---
title: .dqs 파일로 기술 자료 내보내기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81dfc8e7f20fae9dacd521595d101be3117a6794
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647846"
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a><span data-ttu-id="6549b-102">.dqs 파일로 기술 자료 내보내기</span><span class="sxs-lookup"><span data-stu-id="6549b-102">Export a Knowledge Base to a .dqs File</span></span>
  <span data-ttu-id="6549b-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 .dqs 데이터 파일로 전체 기술 자료를 내보내는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-103">This topic describes how to export an entire knowledge base to a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="6549b-104">도메인 또는 전체 기술 자료를 데이터 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="6549b-105">도메인 내보내기에 대한 자세한 내용은 [.dqs 파일로 도메인 내보내기](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6549b-105">For information about exporting a domain, see [Export a Domain to a .dqs File](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="6549b-106">기술 자료를 .dqs 파일로 내보낸 다음 다른 기술 자료로 가져오면 기술 자료 생성 프로세스가 간소화되어 시간과 노력을 절감할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-106">Exporting a knowledge base to a .dqs file, and then importing it as another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="6549b-107">기술 자료와 정보를 다른 사람과 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-107">It enables you to share a knowledge base and its knowledge with others.</span></span> <span data-ttu-id="6549b-108">.dqs 파일에는 연결된 참조 데이터 정보를 제외하고 도메인 및 일치 정책을 포함한 모든 기술 자료 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-108">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="6549b-109">필요한 경우 .dqs 파일을 가져온 후 필요한 도메인을 적절한 참조 데이터 서비스에 다시 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-109">You must attach the required domains to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="6549b-110">기술 자료에 게시된 데이터와 게시되지 않은 데이터를 모두 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-110">Both published and unpublished data in a knowledge base is exported.</span></span>  
  
 <span data-ttu-id="6549b-111">내보내기 프로세스에서 만든 .dqs 데이터 파일은 암호화되므로 내용을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-111">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6549b-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6549b-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6549b-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6549b-113">Prerequisites</span></span>  
 <span data-ttu-id="6549b-114">기술 자료를 .dqs 데이터 파일로 내보내려면 기술 자료를 만들고 열어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-114">To export a knowledge base to a .dqs data file, you must have created and opened a knowledge base.</span></span> <span data-ttu-id="6549b-115">기술 자료를 내보낼 .dqs 파일은 자동으로 생성되므로 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-115">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6549b-116">보안</span><span class="sxs-lookup"><span data-stu-id="6549b-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6549b-117">권한</span><span class="sxs-lookup"><span data-stu-id="6549b-117">Permissions</span></span>  
 <span data-ttu-id="6549b-118">기술 자료를 .dqs 데이터 파일로 내보내려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-118">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a knowledge base to a .dqs data file.</span></span>  
  
##  <a name="export-a-knowledge-base-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="6549b-119">기술 자료를 dqs 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="6549b-119">Export a knowledge base to a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="6549b-120">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-120">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="6549b-121">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 도메인 관리 작업에서 기술 자료를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-121">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="6549b-122">도메인 관리 페이지(원하는 탭 선택)에서 도메인 목록 위의 **기술 자료 데이터를 내보냅니다** 아이콘을 클릭한 다음 **기술 자료 내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-122">In the Domain Management page (with any tab selected), click the **Export Knowledge Base data** icon above the Domain list, and then click **Export Knowledge Base**.</span></span> <span data-ttu-id="6549b-123">또는 **도메인** 목록에서 마우스 오른쪽 단추를 클릭하고 **내보내기**위로 마우스를 이동한 후 **기술 자료 내보내기**를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-123">Alternatively, you can also right-click in the **Domain** list, hover over **Export**, and then click **Export Knowledge Base**.</span></span>  
  
4.  <span data-ttu-id="6549b-124">**데이터 파일로 내보내기** 대화 상자에서 파일을 저장할 폴더로 이동하여 파일의 이름을 지정하거나 기술 자료 이름을 유지한 후 **다른 이름으로 저장** 형식으로 **DQS 데이터 파일(\*.dqs)** 을 지정하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-124">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the knowledge base name, keep **DQS Data Files (\*.dqs)** as the **Save as** type, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="6549b-125">**기술 자료 내보내기** 대화 상자에서 상태 줄에 내보내기가 완료되었다고 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-125">In the **Export Knowledge Base** dialog box, verify that the status line indicates that the export completed.</span></span> <span data-ttu-id="6549b-126">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-126">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a><span data-ttu-id="6549b-127">후속 작업: 도메인을 dqs 파일로 내보낸 후</span><span class="sxs-lookup"><span data-stu-id="6549b-127">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="6549b-128">기술 자료를 .dqs 파일로 내보낸 후 기술 자료를 동일한 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (새 이름 적용) 또는 다른 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549b-128">After you export a knowledge base to a .dqs file, you can import the knowledge base into the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (with a new name) or into a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
  
