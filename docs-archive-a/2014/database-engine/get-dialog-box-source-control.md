---
title: 가져오기 대화 상자 (소스 제어) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.GetVersionDialog
helpviewer_keywords:
- Get dialog box
ms.assetid: 048564d3-6c58-405b-8b57-b690fbfdbe9e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d949a649a35ee3c5a6521223d45975b7c372aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661300"
---
# <a name="get-dialog-box-source-control"></a><span data-ttu-id="8e0fa-102">가져오기 대화 상자(소스 제어)</span><span class="sxs-lookup"><span data-stu-id="8e0fa-102">Get Dialog Box (Source Control)</span></span>
  <span data-ttu-id="8e0fa-103">선택한 항목의 읽기 전용 복사본을 원본 제어 데이터베이스에서 작업 폴더나 지정한 다른 폴더로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-103">Retrieves a read-only copy of the selected item from the source control database to your working folder, or another folder that you specify.</span></span>  
  
## <a name="dialog-box-access"></a><span data-ttu-id="8e0fa-104">대화 상자 액세스</span><span class="sxs-lookup"><span data-stu-id="8e0fa-104">Dialog Box Access</span></span>  
 <span data-ttu-id="8e0fa-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 솔루션 탐색기의 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-105">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], select an item in Solution Explorer.</span></span> <span data-ttu-id="8e0fa-106">**파일** 메뉴에서 **소스 제어** 를 클릭한 다음 **가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-106">On the **File** menu, click **Source Control,** then click **Get**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e0fa-107">이 대화 상자는 솔루션 탐색기의 항목을 마우스 오른쪽 단추로 클릭해도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-107">This dialog box is also available by right-clicking the item in Solution Explorer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e0fa-108">옵션</span><span class="sxs-lookup"><span data-stu-id="8e0fa-108">Options</span></span>  
 <span data-ttu-id="8e0fa-109">**동작**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-109">**Action**</span></span>  
 <span data-ttu-id="8e0fa-110">가져올 항목에 대해 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-110">Specifies the action being performed on the items to retrieve.</span></span>  
  
 <span data-ttu-id="8e0fa-111">**열**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-111">**Columns**</span></span>  
 <span data-ttu-id="8e0fa-112">표시할 열 및 열이 표시되는 순서를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-112">Identifies columns to display and the order in which they are displayed.</span></span>  
  
 <span data-ttu-id="8e0fa-113">**기본 뷰**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-113">**Flat View**</span></span>  
 <span data-ttu-id="8e0fa-114">가져오는 파일을 해당 파일의 원본 제어 연결 아래에 기본 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-114">Display the files you are retrieving as flat lists under their source control connection.</span></span>  
  
 <span data-ttu-id="8e0fa-115">**수정한 시간**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-115">**Modified Time**</span></span>  
 <span data-ttu-id="8e0fa-116">항목을 마지막으로 수정한 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-116">Displays the time when an item was last modified.</span></span>  
  
 <span data-ttu-id="8e0fa-117">**이름**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-117">**Name**</span></span>  
 <span data-ttu-id="8e0fa-118">가져올 항목의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-118">Display the names of the items to retrieve.</span></span> <span data-ttu-id="8e0fa-119">항목은 옆에 있는 확인란이 선택된 상태로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-119">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="8e0fa-120">특정 항목을 가져오지 않으려면 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-120">If you do not want to retrieve a particular item, clear its check box.</span></span>  
  
 <span data-ttu-id="8e0fa-121">**Options**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-121">**Options**</span></span>  
 <span data-ttu-id="8e0fa-122">단추 오른쪽의 화살표를 클릭하면 Source Safe 플러그 인의 가져오기 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-122">Displays source safe plug-in-specific get options when the arrow to the right of the button is clicked.</span></span>  
  
 <span data-ttu-id="8e0fa-123">**Sort**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-123">**Sort**</span></span>  
 <span data-ttu-id="8e0fa-124">표시된 열의 순서를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-124">Sort the order of the displayed columns.</span></span>  
  
 <span data-ttu-id="8e0fa-125">**트리 뷰**</span><span class="sxs-lookup"><span data-stu-id="8e0fa-125">**Tree View**</span></span>  
 <span data-ttu-id="8e0fa-126">검색 중인 항목의 폴더 및 파일 계층 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-126">Display the folder and file hierarchy for the items you are retrieving.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0fa-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e0fa-127">See Also</span></span>  
 <span data-ttu-id="8e0fa-128">[파일 검색](../../2014/database-engine/retrieve-files.md) </span><span class="sxs-lookup"><span data-stu-id="8e0fa-128">[Retrieve Files](../../2014/database-engine/retrieve-files.md) </span></span>  
 [<span data-ttu-id="8e0fa-129">솔루션 탐색기 원본 제어</span><span class="sxs-lookup"><span data-stu-id="8e0fa-129">Solution Explorer Source Control</span></span>](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
