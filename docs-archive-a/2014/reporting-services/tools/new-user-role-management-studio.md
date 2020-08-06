---
title: 새 사용자 역할(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 78201c5ebedd0cdb7f8108b9e6effcaa7fbe87b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732335"
---
# <a name="new-user-role-management-studio"></a><span data-ttu-id="4e9e1-102">새 사용자 역할(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4e9e1-102">New User Role (Management Studio)</span></span>
  <span data-ttu-id="4e9e1-103">이 페이지를 사용하여 항목 수준의 역할 정의를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-103">Use this page to create an item-level role definition.</span></span> <span data-ttu-id="4e9e1-104">항목 수준의 역할 정의란 폴더, 보고서, 모델, 리소스 및 공유 데이터 원본과 관련하여 사용자가 수행할 수 있는 태스크를 열거하는 작업의 명명된 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-104">An item-level role definition is a named collection of tasks that enumerate the tasks a user can perform in relation to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="4e9e1-105">항목 수준의 역할 정의의 예로 보고서 최종 사용자가 폴더를 이동하고 보고서를 보는 데 필요한 동작 종류를 식별하는 미리 정의된 브라우저 역할을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-105">An example of an item-level role definition is the predefined Browser role that identifies the kinds of actions a report end user might require for navigating folders and viewing reports.</span></span>  
  
 <span data-ttu-id="4e9e1-106">역할 정의 개수는 적은 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-106">Role definitions are intended to be few in number.</span></span> <span data-ttu-id="4e9e1-107">대부분의 조직에는 서너 개의 역할 정의만 있으면 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-107">Most organizations only require a few role definitions.</span></span> <span data-ttu-id="4e9e1-108">그러나 미리 정의된 역할 정의가 불충분할 경우 수정하거나 새로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-108">However, if the predefined role definitions are insufficient, you can vary them or create new ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e9e1-109">역할 정의는 기본 모드로 실행되는 보고서 서버에만 사용되며</span><span class="sxs-lookup"><span data-stu-id="4e9e1-109">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="4e9e1-110">보고서 서버가 SharePoint 통합 모드로 구성된 경우 이 페이지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-110">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e9e1-111">옵션</span><span class="sxs-lookup"><span data-stu-id="4e9e1-111">Options</span></span>  
 <span data-ttu-id="4e9e1-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="4e9e1-112">**Name**</span></span>  
 <span data-ttu-id="4e9e1-113">역할 정의의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-113">Type the name of the role definition.</span></span> <span data-ttu-id="4e9e1-114">역할 정의 이름은 보고서 서버 네임스페이스 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-114">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="4e9e1-115">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-115">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="4e9e1-116">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-116">It can also include spaces and some symbols.</span></span> <span data-ttu-id="4e9e1-117">이름 지정 시에는 다음 문자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-117">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="4e9e1-118">; ?</span><span class="sxs-lookup"><span data-stu-id="4e9e1-118">; ?</span></span> <span data-ttu-id="4e9e1-119">: \@ & = +, $/\*\< ></span><span class="sxs-lookup"><span data-stu-id="4e9e1-119">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="4e9e1-120">" /</span><span class="sxs-lookup"><span data-stu-id="4e9e1-120">" /</span></span>  
  
 <span data-ttu-id="4e9e1-121">**설명**</span><span class="sxs-lookup"><span data-stu-id="4e9e1-121">**Description**</span></span>  
 <span data-ttu-id="4e9e1-122">역할 사용 방법을 설명하고 역할에서 지원하는 작업을 나열하는 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-122">Type a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="4e9e1-123">**Task**</span><span class="sxs-lookup"><span data-stu-id="4e9e1-123">**Task**</span></span>  
 <span data-ttu-id="4e9e1-124">이 역할을 통해 수행할 수 있는 태스크를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-124">Select the tasks that can be performed through this role.</span></span> <span data-ttu-id="4e9e1-125">새 태스크를 만들거나 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 지원하는 기존 작업을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-125">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="4e9e1-126">항목 수준의 역할 정의에서는 항목 수준의 태스크만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-126">Only item-level tasks can be used in an item-level role definition.</span></span>  
  
 <span data-ttu-id="4e9e1-127">**태스크 설명**</span><span class="sxs-lookup"><span data-stu-id="4e9e1-127">**Task Description**</span></span>  
 <span data-ttu-id="4e9e1-128">작업에서 지원하는 작업 또는 사용 권한을 열거하는 태스크에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-128">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e9e1-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e9e1-129">See Also</span></span>  
 <span data-ttu-id="4e9e1-130">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="4e9e1-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="4e9e1-131">역할 정의</span><span class="sxs-lookup"><span data-stu-id="4e9e1-131">Role Definitions</span></span>](../security/role-definitions.md)  
  
  
