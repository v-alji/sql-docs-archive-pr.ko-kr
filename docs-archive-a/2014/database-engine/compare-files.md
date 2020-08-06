---
title: 파일 비교 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- versions [SQL Server], file comparisons
- comparing files
- file comparisons [SQL Server]
ms.assetid: 728811c4-5d7a-4420-abce-f56c5a0994d2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f29bf7098f0c73d0b672e20b973b1347349b31f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652354"
---
# <a name="compare-files"></a><span data-ttu-id="67b66-102">파일 비교</span><span class="sxs-lookup"><span data-stu-id="67b66-102">Compare Files</span></span>
  <span data-ttu-id="67b66-103">파일을 비교하여 파일이 현재 상태로 진행된 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-103">You can compare files to determine how a file has progressed to its present state.</span></span> <span data-ttu-id="67b66-104">예를 들어 특정 원본 파일 버전이 체크 인된 후에 코드 프로젝트의 작성에서 오류가 발견된 경우 현재 파일 버전을 이전 파일 버전과 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-104">For example, if you detect a defect in a build of your code project after a particular source file version is checked in, you can compare the current file version to a previous one.</span></span> <span data-ttu-id="67b66-105">이렇게 하면 오류를 일으킨 코드를 찾아낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-105">This helps you to pinpoint the code that introduced the defect.</span></span>  
  
 <span data-ttu-id="67b66-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 프로젝트나 파일의 로컬 복사본을 원본 제어에 저장된 버전과 비교하거나 두 개의 로컬 파일을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-106">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to compare a local copy of a project or file to the version stored in source control, or to compare two local files.</span></span> <span data-ttu-id="67b66-107">또한 **History** 명령을 사용 하면 소스 제어에서 사용 하는 두 버전을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-107">Also, using the **History** command, you can compare any two source-controlled versions.</span></span>  
  
### <a name="to-compare-files"></a><span data-ttu-id="67b66-108">파일을 비교하려면</span><span class="sxs-lookup"><span data-stu-id="67b66-108">To compare files</span></span>  
  
1.  <span data-ttu-id="67b66-109">솔루션 탐색기에서 프로젝트나 프로젝트 파일 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-109">In Solution Explorer, select either a project or one of the project files.</span></span>  
  
2.  <span data-ttu-id="67b66-110">**파일** 메뉴에서 **원본 제어**를 가리킨 다음 **비교**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-110">On the **File** menu, point to **Source Control**, and click **Compare**.</span></span>  
  
3.  <span data-ttu-id="67b66-111">**차이 옵션** 대화 상자에서 적절 한 옵션을 선택한 다음 **보고서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="67b66-111">In the **Difference Options** dialog box, select the appropriate options, and then click **Report**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b66-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67b66-112">See Also</span></span>  
 <span data-ttu-id="67b66-113">[버전 정보 설정 및 검색](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="67b66-113">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="67b66-114">[파일 기록 보기](../../2014/database-engine/view-file-history.md) </span><span class="sxs-lookup"><span data-stu-id="67b66-114">[View File History](../../2014/database-engine/view-file-history.md) </span></span>  
 <span data-ttu-id="67b66-115">[프로젝트 기록 보기](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="67b66-115">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 <span data-ttu-id="67b66-116">[파일 상태 보기](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="67b66-116">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 [<span data-ttu-id="67b66-117">파일 검색</span><span class="sxs-lookup"><span data-stu-id="67b66-117">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
  
