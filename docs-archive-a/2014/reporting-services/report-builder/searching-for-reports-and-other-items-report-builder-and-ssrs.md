---
title: 보고서 및 기타 항목 검색(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a964cbdbc674fb3d29e18b5e5075695f0033801e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639357"
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a><span data-ttu-id="4b1f6-102">보고서 및 기타 항목 검색(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="4b1f6-102">Searching for Reports and Other Items (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="4b1f6-103">보고서 관리자를 사용하여 보고서 서버에서 이름이나 설명을 기준으로 특정 항목을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-103">You can use Report Manager to search a report server for specific items by name or description.</span></span> <span data-ttu-id="4b1f6-104">게시된 보고서, 보고서 모델, 폴더, 공유 데이터 원본 및 리소스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-104">You can search for published reports, report models, folders, shared data sources, and resources.</span></span> <span data-ttu-id="4b1f6-105">일정, 소유자, 역할 할당, 보고서 기록의 특정 스냅샷 또는 구독은 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-105">You cannot search for schedules, owners, role assignments, specific snapshots in report history, or subscriptions.</span></span> <span data-ttu-id="4b1f6-106">검색은 항목이 저장되는 보고서 서버 데이터베이스에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-106">The search is performed on the report server database where the items are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b1f6-107">파일 시스템을 검색해도 보고서 서버에서 관리되는 항목에 대한 검색 결과는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-107">Performing a file system search will not return search results for items managed by a report server.</span></span>  
  
-   <span data-ttu-id="4b1f6-108">보고서 관리자에서 항목을 검색하려면 페이지 위쪽의 **검색 대상** 입력란에 검색 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-108">To search for items in Report Manager, type a search string in the **Search for** text box at the top of the page.</span></span> <span data-ttu-id="4b1f6-109">검색은 폴더 계층의 최상위 노드에서 시작되어 모든 분기를 따라 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-109">Searches begin at the top node in the folder hierarchy and then proceed through every branch.</span></span> <span data-ttu-id="4b1f6-110">특정 분기에 대한 액세스 권한이 없는 경우 해당 분기는 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-110">If you do not have permission to access a specific branch, that branch is skipped.</span></span> <span data-ttu-id="4b1f6-111">다른 사용자에게 속한 내 보고서 폴더와 일반적으로 사용할 수 없는 다른 폴더도 같은 방식으로 검색을 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-111">This applies to My Reports folders that belong to other users, and to other folders that are not generally available.</span></span> <span data-ttu-id="4b1f6-112">보기 권한이 있는 보고서와 항목만 검색 결과에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-112">Only reports and items that you have permission to view are included in the search results.</span></span>  
  
-   <span data-ttu-id="4b1f6-113">이름이나 설명을 기준으로 항목을 검색하려면 검색할 텍스트 전부 또는 일부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-113">To search for an item by name or description, specify all or part of the text that you want to match.</span></span> <span data-ttu-id="4b1f6-114">검색 문자열은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-114">The search string is not case-sensitive.</span></span> <span data-ttu-id="4b1f6-115">검색 조건을 포함하거나 제외하기 위해 더하기(+) 또는 빼기(-) 기호와 같은 검색 연산자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-115">You cannot use search operators such as plus (+) or minus (-) symbols to require or exclude search criteria.</span></span>  
  
-   <span data-ttu-id="4b1f6-116">보고서에서 특정 텍스트를 검색하려면 보고서 위쪽의 도구 모음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4b1f6-116">To search for specific text within a report, use the toolbar at the top of the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b1f6-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b1f6-117">See Also</span></span>  
 <span data-ttu-id="4b1f6-118">[보고서 관리자 &#40;보고서 작성기 및 SSRS에서 보고서 찾기 및 보기&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b1f6-118">[Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b1f6-119">[내 보고서 &#40;보고서 작성기 및 SSRS를 사용 하 여&#41;](using-my-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b1f6-119">[Using My Reports &#40;Report Builder and SSRS&#41;](using-my-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b1f6-120">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b1f6-120">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4b1f6-121">보고서 열기 및 닫기&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="4b1f6-121">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)  
  
  
