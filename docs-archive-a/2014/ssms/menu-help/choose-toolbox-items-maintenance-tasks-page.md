---
title: 도구 상자 항목 선택(유지 관리 태스크 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vs.chooseitems.maintenance_tasks
- VS.ToolboxPages.Maintenance_Tasks
helpviewer_keywords:
- Customize Toolbox dialog box
ms.assetid: b92c9054-7479-45d8-a54c-c1bb6699bdb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28c90cd0abc76a7ae721ff0580aa119c3c5639b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733451"
---
# <a name="choose-toolbox-items-maintenance-tasks-page"></a><span data-ttu-id="8252b-102">도구 상자 항목 선택(유지 관리 태스크 페이지)</span><span class="sxs-lookup"><span data-stu-id="8252b-102">Choose Toolbox Items (Maintenance Tasks Page)</span></span>
  <span data-ttu-id="8252b-103">**도구 상자 사용자 지정** 대화 상자의 이 탭에는 컴퓨터에 등록되어 있는 모든 유지 관리 태스크 구성 요소의 목록이 표시되며 이 탭을 사용하여 도구 상자에 표시되는 구성 요소를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-103">This tab of the **Customize Toolbox** dialog box displays a list of all maintenancetask components registered on your computer and makes it possible for you to change the ones that are displayed in the Toolbox.</span></span> <span data-ttu-id="8252b-104">**도구 상자 사용자 지정** 대화 상자는 **도구** 메뉴에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-104">You can open the **Customize Toolbox** dialog box from the **Tools** menu.</span></span> <span data-ttu-id="8252b-105">구성 요소 목록을 정렬하려면 열 머리글 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-105">To sort the list of components, select any column heading.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8252b-106">옵션</span><span class="sxs-lookup"><span data-stu-id="8252b-106">Options</span></span>  
 <span data-ttu-id="8252b-107">**유지 관리 태스크** 탭에는 다음 정보 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-107">The **Maintenance Tasks** tab includes the following columns of information.</span></span>  
  
 <span data-ttu-id="8252b-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="8252b-108">**Name**</span></span>  
 <span data-ttu-id="8252b-109">사용 가능한 구성 요소의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-109">Displays the names of available components.</span></span> <span data-ttu-id="8252b-110">각 이름 앞에는 확인란이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-110">Preceding each name is a check box.</span></span> <span data-ttu-id="8252b-111">이 확인란이 선택되어 있으면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 가 컴퓨터의 레지스트리에서 해당 구성 요소에 대한 항목을 발견한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-111">If selected, a check box indicates that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has found an entry for the component in your computer's registry.</span></span> <span data-ttu-id="8252b-112">구성 요소는 활성 **도구 상자** 탭에 이미 표시되어 있거나, 표시되어 있지 않을 경우 **확인**을 클릭하면 해당 탭에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-112">The component is either already displayed on the active **Toolbox** tab, or it will be added to it when you click **OK**.</span></span> <span data-ttu-id="8252b-113">확인란이 선택되어 있지 않으면 구성 요소가 현재 **도구 상자**에 표시되어 있지 않거나 **확인** 을 클릭하면 **도구 상자**에서 제거된다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-113">If cleared, a check box indicates that the component is not currently displayed in the **Toolbox**, or that it will be removed from the **Toolbox** when you click **OK**.</span></span>  
  
 <span data-ttu-id="8252b-114">**Path**</span><span class="sxs-lookup"><span data-stu-id="8252b-114">**Path**</span></span>  
 <span data-ttu-id="8252b-115">구성 요소의 전체 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-115">Displays the full path to the component.</span></span> <span data-ttu-id="8252b-116">제품과 함께 제공된 기본 구성 요소를 확인하려면 이 열을 정렬한 다음 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 설치 경로에 저장되어 있는 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-116">To identify the default components that shipped with the product, sort on this column and then locate those stored on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio installation path.</span></span>  
  
 <span data-ttu-id="8252b-117">**마지막으로 수정한 날짜**</span><span class="sxs-lookup"><span data-stu-id="8252b-117">**Last Modified**</span></span>  
 <span data-ttu-id="8252b-118">구성 요소를 마지막으로 수정한 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-118">Displays the date when the component was last modified.</span></span>  
  
 <span data-ttu-id="8252b-119">**언어** 및 **버전** 상자에 구성 요소의 특성을 아이콘과 함께 표시하려면 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-119">Click on a name to show the attributes of the component in the **Language** and **Version** boxes, along with the icon.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8252b-120">옵션</span><span class="sxs-lookup"><span data-stu-id="8252b-120">Options</span></span>  
 <span data-ttu-id="8252b-121">**언어**</span><span class="sxs-lookup"><span data-stu-id="8252b-121">**Language**</span></span>  
 <span data-ttu-id="8252b-122">구성 요소의 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-122">The language of the component.</span></span>  
  
 <span data-ttu-id="8252b-123">**버전**</span><span class="sxs-lookup"><span data-stu-id="8252b-123">**Version**</span></span>  
 <span data-ttu-id="8252b-124">구성 요소의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8252b-124">The version of the component.</span></span>  
  
  
