---
title: 개체 선택(개체 탐색기) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.selectobjects.f1
ms.assetid: 692477fe-dd7c-403d-acd2-bb108b6077f1
author: stevestein
ms.author: sstein
ms.openlocfilehash: ceec604d9fe07b339af11ed69226d41a7f616678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727859"
---
# <a name="select-objects-object-explorer"></a><span data-ttu-id="4fb86-102">개체 선택(개체 탐색기)</span><span class="sxs-lookup"><span data-stu-id="4fb86-102">Select Objects (Object Explorer)</span></span>
  <span data-ttu-id="4fb86-103">**개체 선택** 대화 상자를 사용하여 다른 대화 상자에 있는 목록에 개체를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-103">Use the **Select Objects** dialog box to add an object to a list in another dialog box.</span></span> <span data-ttu-id="4fb86-104">대화 상자 제목과 대화 상자에서 사용할 수 있는 옵션은 대화 상자를 연 방법에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-104">The dialog box title and the options available in the dialog box depend upon how it was opened.</span></span> <span data-ttu-id="4fb86-105">사용 가능한 옵션만 나타납니다. 예를 들어 새 개체의 소유자를 선택하는 경우에는 로그인만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-105">Only available options appear; for instance, only logins are available when you are selecting an owner for a new object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4fb86-106">옵션</span><span class="sxs-lookup"><span data-stu-id="4fb86-106">Options</span></span>  
 <span data-ttu-id="4fb86-107">**개체 유형 선택**</span><span class="sxs-lookup"><span data-stu-id="4fb86-107">**Select these object types**</span></span>  
 <span data-ttu-id="4fb86-108">선택할 개체가 속한 유형 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-108">Displays a list of the types of which the objects to be selected belong.</span></span> <span data-ttu-id="4fb86-109">유형에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 수준과 데이터베이스 수준의 보안 주체 및 보안 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-109">The types include [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] level and database level principals and securables.</span></span> <span data-ttu-id="4fb86-110">이 상자는 **개체 유형** 단추를 클릭하여 액세스할 수 있는 **개체 유형 선택** 대화 상자에서 선택한 항목으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-110">This box is populated from the selections made from the **Select Object Types** dialog box, accessed from the **Objects Type** button.</span></span>  
  
 <span data-ttu-id="4fb86-111">**선택할 개체 이름을 입력하십시오.**</span><span class="sxs-lookup"><span data-stu-id="4fb86-111">**Enter the object names to select**</span></span>  
 <span data-ttu-id="4fb86-112">선택할 개체 이름 목록을 세미콜론으로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-112">Enter a semicolon-separated list of names of the objects to be selected.</span></span> <span data-ttu-id="4fb86-113">선택할 개체는 **개체 유형 선택** 상자에 나열된 유형이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-113">Objects to be selected must be of a type listed in the **Select these object types** box.</span></span> <span data-ttu-id="4fb86-114">**찾아보기** 단추를 클릭하여 액세스할 수 있는 목록에서 개체를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-114">Objects can be selected from a list accessed by clicking the **Browse** button.</span></span>  
  
 <span data-ttu-id="4fb86-115">**개체 유형**</span><span class="sxs-lookup"><span data-stu-id="4fb86-115">**Object Types**</span></span>  
 <span data-ttu-id="4fb86-116">개체 유형 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-116">Displays a list of object types.</span></span> <span data-ttu-id="4fb86-117">해당 확인란을 선택하여 하나 이상의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-117">Select one or more by selecting the check box corresponding to the type.</span></span>  
  
 <span data-ttu-id="4fb86-118">**이름 확인**</span><span class="sxs-lookup"><span data-stu-id="4fb86-118">**Check Names**</span></span>  
 <span data-ttu-id="4fb86-119">**선택할 개체 이름을 입력하십시오.** 상자에 있는 개체 이름의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-119">Validates the object names in the **Enter the object names to select** box.</span></span> <span data-ttu-id="4fb86-120">유효하지 않은 개체 이름이 나열된 경우 **이름을 찾을 수 없음** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-120">If an object name that is not valid is listed, the **Name not Found** dialog box is presented.</span></span> <span data-ttu-id="4fb86-121">이 대화 상자를 사용하여 선택할 개체 목록에서 이름을 수정하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-121">With this dialog box, the name can be corrected or removed from the list of objects to select.</span></span>  
  
 <span data-ttu-id="4fb86-122">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="4fb86-122">**Browse**</span></span>  
 <span data-ttu-id="4fb86-123">**개체 찾아보기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-123">Presents the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="4fb86-124">이 대화 상자에는 **개체 유형 선택** 상자에 나열된 유형의 개체 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-124">This contains a list of objects of the types listed in the **Select These Object Types** box.</span></span> <span data-ttu-id="4fb86-125">해당 확인란을 선택하여 이 목록에서 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb86-125">Select objects from this list by selecting the corresponding check boxes.</span></span>  
  
  
