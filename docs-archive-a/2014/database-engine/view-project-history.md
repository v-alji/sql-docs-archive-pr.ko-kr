---
title: 프로젝트 기록 보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing project history
- version control services [SQL Server], project history
- projects [SQL Server Management Studio], historical information
- historical information [SQL Server], projects
ms.assetid: be0ea2ac-4a35-429c-9c9e-4001ea9035a4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85028141050e19e6ed6394a5bb17709ac8f906ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660700"
---
# <a name="view-project-history"></a><span data-ttu-id="97b0f-102">프로젝트 기록 보기</span><span class="sxs-lookup"><span data-stu-id="97b0f-102">View Project History</span></span>
  <span data-ttu-id="97b0f-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] VSS(Visual SourceSafe) 프로젝트의 기록에는 파일 작성, 추가, 삭제, 복구 등을 비롯하여 각 프로젝트 파일에서 수행된 모든 동작의 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-103">The history of a [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) project includes a list of all the actions taken on each of the project files, including file creation, addition, deletion, and recovery.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97b0f-104">Visual SourceSaf 프로젝트는 일반적으로 원본 제어 서버 폴더라 불립니다. 이 폴더는 원본 제어 파일의 서버 버전이 서버에 저장되는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-104">A Visual SourceSafe project is more commonly referred to as the source control server folder, the location where the server version of a source-controlled file is stored on the server.</span></span>  
  
 <span data-ttu-id="97b0f-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 현재 로드된 솔루션이 속하는 Visual SourceSafe 프로젝트의 기록을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-105">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to examine the history of the Visual SourceSafe project to which the currently loaded solution belongs.</span></span> <span data-ttu-id="97b0f-106">프로젝트 기록의 일부로 표시되는 정보에 기초하여 파일 버전의 로컬 복사본을 검색하거나 삭제된 버전을 복원하거나 프로젝트 간에 파일 버전을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-106">Based on the information displayed as part of the history of a project, you can retrieve local copies of file versions, restore deleted versions, or share a file version between projects.</span></span>  
  
### <a name="to-view-the-history-of-a-vss-project"></a><span data-ttu-id="97b0f-107">VSS 프로젝트의 기록을 보려면</span><span class="sxs-lookup"><span data-stu-id="97b0f-107">To view the history of a VSS project</span></span>  
  
1.  <span data-ttu-id="97b0f-108">솔루션 탐색기에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="97b0f-109">**파일** 메뉴에서 **소스 제어** 를 가리킨 다음 **기록 보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-109">On the **File** menu, point to **Source Control** and click **View History**.</span></span>  
  
3.  <span data-ttu-id="97b0f-110">**기록** \<Project> 대화 상자에서 다음 작업 중 하나를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-110">In the **History of** \<Project> dialog box, perform any of the following actions:</span></span>  
  
    -   <span data-ttu-id="97b0f-111">선택한 파일에 대한 원본 제어 시스템의 복사본을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-111">View the source control system's copy of a selected file.</span></span>  
  
    -   <span data-ttu-id="97b0f-112">선택한 파일에 대한 세부 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-112">View detailed information about a selected file.</span></span>  
  
    -   <span data-ttu-id="97b0f-113">선택한 파일을 로컬 디스크로 읽어 들입니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-113">Retrieve a selected file to your local disk.</span></span>  
  
    -   <span data-ttu-id="97b0f-114">선택한 파일을 체크 아웃합니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-114">Check out a selected file.</span></span>  
  
    -   <span data-ttu-id="97b0f-115">선택한 파일을 두 원본 제어 프로젝트 간에 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-115">Share a selected file between two source control projects.</span></span>  
  
    -   <span data-ttu-id="97b0f-116">기록 보고서를 프린터, 파일 또는 클립보드에 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="97b0f-116">Export the history report to a printer, a file, or the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b0f-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97b0f-117">See Also</span></span>  
 <span data-ttu-id="97b0f-118">[버전 정보 설정 및 검색](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="97b0f-118">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="97b0f-119">[파일 상태 보기](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="97b0f-119">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 <span data-ttu-id="97b0f-120">[파일 검색](../../2014/database-engine/retrieve-files.md) </span><span class="sxs-lookup"><span data-stu-id="97b0f-120">[Retrieve Files](../../2014/database-engine/retrieve-files.md) </span></span>  
 [<span data-ttu-id="97b0f-121">파일 비교</span><span class="sxs-lookup"><span data-stu-id="97b0f-121">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
  
