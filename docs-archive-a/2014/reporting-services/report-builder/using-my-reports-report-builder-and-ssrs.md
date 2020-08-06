---
title: 내 보고서 사용(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91d44c0aa8471064753d9b4fb0ecc0de89aa8396
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648808"
---
# <a name="using-my-reports-report-builder-and-ssrs"></a><span data-ttu-id="d6056-102">내 보고서 사용(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d6056-102">Using My Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d6056-103">기본 모드로 구성된 보고서 서버에서 내 보고서 폴더는 소유한 보고서를 저장하고 작업하는 데 사용할 수 있는 개인 작업 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-103">On a report server configured in native mode, the My Reports folder is a personal workspace that you can use to store and work with reports that you own.</span></span> <span data-ttu-id="d6056-104">다른 보고서 서버 폴더는 공용 폴더이며 일반적으로 사용자가 폴더 내용을 추가하거나 수정하려면 고급 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-104">Other report server folders are public and typically require users to have advanced permissions to add to or modify folder contents.</span></span> <span data-ttu-id="d6056-105">이와는 달리 내 보고서 폴더는 사용자 관리 작업 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-105">In contrast, the My Reports folder is a user-managed workspace.</span></span> <span data-ttu-id="d6056-106">보고서와 폴더를 추가하거나 제거할 수 있으며 사용자 개인 설정을 사용하여 링크된 보고서를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-106">You can add or remove reports and folders and save linked reports with personalized settings.</span></span>  
  
 <span data-ttu-id="d6056-107">개념적으로 내 보고서 폴더는 Windows 파일 시스템의 내 문서 폴더와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-107">Conceptually, the My Reports folder is similar to the My Documents folder in the Windows file system.</span></span> <span data-ttu-id="d6056-108">각 사용자가 내 보고서라는 폴더를 가지고 있더라도 액세스하는 폴더는 모두 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-108">Although each user has a folder called My Reports, the folder that each accesses is different from all other users.</span></span> <span data-ttu-id="d6056-109">보고서 서버 관리자를 제외한 사용자는 다른 사용자가 소유한 내 보고서 폴더의 내용에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-109">Except for report server administrators, other users cannot access the contents of the My Reports folder that belongs to you.</span></span>  
  
 <span data-ttu-id="d6056-110">내 보고서 기능은 선택적이며 보고서 서버 관리자가 설정을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-110">The My Reports feature is optional and can be disabled by a report server administrator.</span></span> <span data-ttu-id="d6056-111">이 기능을 설정하면 홈 폴더에 내 보고서 폴더가 나타나며 보고서 관리자나 웹 브라우저를 사용하여 이 폴더에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-111">If it is enabled, you will see a My Reports folder in the Home folder, which you can access using the Report Manager or a Web browser.</span></span> <span data-ttu-id="d6056-112">자세한 내용은 [보고서 관리자에서 보고서 찾기 및 보기&#40;보고서 작성기 및 SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6056-112">For more information, see [Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="d6056-113">SharePoint 통합 모드로 구성된 보고서 서버에는 내 보고서 폴더에 해당하는 폴더가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-113">On a report server configured in SharePoint integrated mode, there is no equivalent to the My Reports folder.</span></span> <span data-ttu-id="d6056-114">자세한 내용은 [보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6056-114">For more information, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a><span data-ttu-id="d6056-115">내 보고서 사용 방법</span><span class="sxs-lookup"><span data-stu-id="d6056-115">Ways to Use My Reports</span></span>  
 <span data-ttu-id="d6056-116">사용자가 보고서, 폴더 및 기타 항목을 추가할 때까지는 내 보고서가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-116">My Reports is empty until you add reports, folders, and other items.</span></span> <span data-ttu-id="d6056-117">내 보고서에 내용을 추가하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-117">Here are some ways to add content to My Reports.</span></span>  
  
-   <span data-ttu-id="d6056-118">링크된 개인 보고서를 만들어 내 보고서에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-118">Create a personal linked report and store it in My Reports.</span></span> <span data-ttu-id="d6056-119">일부 보고서는 링크로 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-119">Not all reports are available for linking.</span></span> <span data-ttu-id="d6056-120">자세한 내용은 [연결된 보고서 만들기](../reports/create-a-linked-report.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6056-120">For more information, see [Create a Linked Report](../reports/create-a-linked-report.md).</span></span>  
  
-   <span data-ttu-id="d6056-121">파일 시스템에서 보고서 정의 파일(.rdl), 보고서 모델 파일(.smdl) 또는 기타 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-121">Upload a report definition (.rdl) file, report model (.smdl) file, or other files from the file system.</span></span> <span data-ttu-id="d6056-122">모든 파일을 업로드할 수 있지만 보고서 서버에서는 파일 확장명이 .rdl 또는 .smdl인 보고서 파일만 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-122">You can upload any file, but the report server only processes report files that have an .rdl or .smdl file extension.</span></span> <span data-ttu-id="d6056-123">자세한 내용은 SQL Server 온라인 설명서의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에서 “보고서 정의” 및 [파일 또는 보고서 업로드&#40;보고서 관리자&#41;](../reports/upload-a-file-or-report-report-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6056-123">For more information, see Report Definitions" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  
-   <span data-ttu-id="d6056-124">사용자 보고서를 만들어 내 보고서에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-124">Create and publish your own reports to My Reports.</span></span> <span data-ttu-id="d6056-125">자세한 내용은 [보고서 디자인 뷰&#40;보고서 작성기&#41;](report-design-view-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6056-125">For more information, see [Report Design View &#40;Report Builder&#41;](report-design-view-report-builder.md).</span></span>  
  
 <span data-ttu-id="d6056-126">일반적으로 내 보고서에 대한 사용 권한으로 폴더를 직접 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-126">Usually, permissions on My Reports allow you to manage the folder yourself.</span></span> <span data-ttu-id="d6056-127">그러나 사용자가 수행할 수 있는 태스크는 보고서 서버 관리자가 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-127">However, the report server administrator ultimately determines which tasks users can perform.</span></span> <span data-ttu-id="d6056-128">사용 권한이 부족하여 내 보고서에서 작업할 수 없는 경우 보고서 서버 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6056-128">If insufficient permissions prevent you from working with My Reports, see your report server administrator.</span></span>  
  
## <a name="searching-my-reports"></a><span data-ttu-id="d6056-129">내 보고서 검색</span><span class="sxs-lookup"><span data-stu-id="d6056-129">Searching My Reports</span></span>  
 <span data-ttu-id="d6056-130">보고서 서버 데이터베이스를 검색할 때 검색 범위에 해당 사용자의 내 보고서 폴더 내용만 포함되고 다른 사용자의 내 보고서 폴더 내용은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-130">When you search a report server database, the contents of your My Reports folder are included in the search, while the contents of other user's My Reports folders are excluded.</span></span> <span data-ttu-id="d6056-131">검색 결과에는 사용자가 액세스할 수 있는 보고서만 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6056-131">Search results list only the reports to which you have access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6056-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6056-132">See Also</span></span>  
 [<span data-ttu-id="d6056-133">보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6056-133">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
