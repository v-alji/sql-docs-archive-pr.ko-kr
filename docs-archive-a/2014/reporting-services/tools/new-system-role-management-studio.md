---
title: 새 시스템 역할(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a744fc78bdd5ae6ef3a37f96ff5ae8cd10f71a80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732336"
---
# <a name="new-system-role-management-studio"></a><span data-ttu-id="696ba-102">새 시스템 역할(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="696ba-102">New System Role (Management Studio)</span></span>
  <span data-ttu-id="696ba-103">이 페이지를 사용하여 시스템 수준의 역할 정의를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-103">Use this page to create a system-level role definition.</span></span> <span data-ttu-id="696ba-104">시스템 역할 정의는 보고서 서버 전체에 적용되는 시스템 수준 태스크 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-104">A system role definition specifies a set of system-level tasks that apply to a report server as whole.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="696ba-105">역할 정의는 기본 모드로 실행되는 보고서 서버에만 사용되며</span><span class="sxs-lookup"><span data-stu-id="696ba-105">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="696ba-106">보고서 서버가 SharePoint 통합 모드로 구성된 경우 이 페이지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-106">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="696ba-107">옵션</span><span class="sxs-lookup"><span data-stu-id="696ba-107">Options</span></span>  
 <span data-ttu-id="696ba-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="696ba-108">**Name**</span></span>  
 <span data-ttu-id="696ba-109">역할 정의의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-109">Type the name of the role definition.</span></span> <span data-ttu-id="696ba-110">역할 정의 이름은 보고서 서버 네임스페이스 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-110">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="696ba-111">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-111">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="696ba-112">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-112">It can also include spaces and some symbols.</span></span> <span data-ttu-id="696ba-113">이름 지정 시에는 다음 문자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="696ba-113">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="696ba-114">; ?</span><span class="sxs-lookup"><span data-stu-id="696ba-114">; ?</span></span> <span data-ttu-id="696ba-115">: \@ & = +, $/\*\< ></span><span class="sxs-lookup"><span data-stu-id="696ba-115">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="696ba-116">" /</span><span class="sxs-lookup"><span data-stu-id="696ba-116">" /</span></span>  
  
 <span data-ttu-id="696ba-117">**설명**</span><span class="sxs-lookup"><span data-stu-id="696ba-117">**Description**</span></span>  
 <span data-ttu-id="696ba-118">역할 사용 방법을 설명하고 역할에서 지원하는 작업을 나열하는 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-118">Provide a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="696ba-119">**Task**</span><span class="sxs-lookup"><span data-stu-id="696ba-119">**Task**</span></span>  
 <span data-ttu-id="696ba-120">이 역할을 통해 수행할 수 있는 시스템 수준의 태스크를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-120">Select the system-level tasks that can be performed through this role.</span></span> <span data-ttu-id="696ba-121">새 태스크를 만들거나 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 지원하는 기존 작업을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-121">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="696ba-122">또한 시스템 역할 정의에 대해 항목 수준의 태스크를 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-122">You cannot choose item-level tasks for a system role definition.</span></span>  
  
 <span data-ttu-id="696ba-123">**태스크 설명**</span><span class="sxs-lookup"><span data-stu-id="696ba-123">**Task Description**</span></span>  
 <span data-ttu-id="696ba-124">작업에서 지원하는 작업 또는 사용 권한을 열거하는 태스크에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="696ba-124">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696ba-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="696ba-125">See Also</span></span>  
 <span data-ttu-id="696ba-126">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="696ba-126">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="696ba-127">역할 정의</span><span class="sxs-lookup"><span data-stu-id="696ba-127">Role Definitions</span></span>](../security/role-definitions.md)  
  
  
