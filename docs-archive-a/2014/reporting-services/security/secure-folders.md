---
title: 보안 폴더 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high-security folders [Reporting Services]
- low-security folders
- folders [Reporting Services], security
- security [Reporting Services], folders
ms.assetid: 0fd91f77-0143-476b-9af0-87293be78e44
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483b3108713032b3aaf566208f39f6c2f705da1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648258"
---
# <a name="secure-folders"></a><span data-ttu-id="2e2de-102">보안 폴더</span><span class="sxs-lookup"><span data-stu-id="2e2de-102">Secure Folders</span></span>
  <span data-ttu-id="2e2de-103">폴더 보안 설정은 보고서 서버의 모든 내용에 보안을 설정하기 위한 기본 토대입니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-103">Folder security is the foundation for securing all content in a report server.</span></span> <span data-ttu-id="2e2de-104">보안 설정은 폴더 구조를 통해 상속되므로 폴더 계층의 큰 부분이나 작은 부분을 지정하여 특정 종류의 액세스를 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-104">Because security is inherited throughout the folder structure, you can designate large or small sections of the folder hierarchy to allow for certain kinds of access.</span></span>  
  
 <span data-ttu-id="2e2de-105">보안 설정이 높은 폴더는 기밀 보고서를 저장하거나 준비 영역으로 사용할 수 있습니다. 예를 들어 보고서를 최종 위치로 이동하기 전에 보고서 테스트용으로 폴더를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-105">High-security folders can be used to store confidential reports or as staging areas; for example, you can have a folder that you use to test reports before moving them to a final location.</span></span> <span data-ttu-id="2e2de-106">이 영역에 대한 액세스를 제어하려면 보고서 작성자만 항목을 추가하고 삭제할 수 있도록 하는 하나의 역할 할당과 테스터가 보고서 실행은 할 수 있지만 항목을 추가하거나 제거할 수 없도록 하는 또 다른 역할 할당을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-106">To control access to this area, you can define one role assignment that allows only report authors to add and delete items, and a second role assignment that allows testers to run reports but not to add or remove items.</span></span> <span data-ttu-id="2e2de-107">역할 할당이 테스터 및 보고서 작성자에 대해 명시적으로 정의되므로 로컬 시스템 관리자를 제외한 다른 사용자는 폴더에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-107">Because the role assignments are defined explicitly for testers and report authors, no other users (except for local system administrators) can access the folder.</span></span>  
  
 <span data-ttu-id="2e2de-108">보안 설정이 낮은 폴더는 쉽게 액세스할 수 있는 보고서를 저장하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-108">Low-security folders can be used to store reports that you want to be easily accessible.</span></span>  
  
 <span data-ttu-id="2e2de-109">폴더 보안 설정은 보고서 서버 폴더 계층의 루트 노드인 홈 폴더에서 시작하는 항목 수준의 보안의 기본을 이룹니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-109">Folder security forms the basis of item-level security, starting with the root node of the report server folder hierarchy, the Home folder.</span></span> <span data-ttu-id="2e2de-110">보안 설정은 상속되므로 홈 폴더에 대해 적정 수준으로 제한된 보안 정책을 설정하는 게 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-110">Because security is inherited, it is advisable to set a fairly restrictive security policy on the Home folder.</span></span> <span data-ttu-id="2e2de-111">홈 폴더 역할 할당에 **브라우저** 역할을 사용하면 보기 전용 액세스를 제공하여 보안 정책이 적절히 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-111">Using the **Browser** role in Home folder role assignments does exactly that by providing view-only access.</span></span>  
  
## <a name="tasks-and-folder-access"></a><span data-ttu-id="2e2de-112">태스크 및 폴더 액세스</span><span class="sxs-lookup"><span data-stu-id="2e2de-112">Tasks and Folder Access</span></span>  
 <span data-ttu-id="2e2de-113">폴더에 대한 역할 할당을 만들 때는 다음 표에 나열된 태스크를 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e2de-113">When creating role assignments for folders, consider the tasks listed in the following table.</span></span>  
  
|<span data-ttu-id="2e2de-114">태스크 선택</span><span class="sxs-lookup"><span data-stu-id="2e2de-114">Select this task</span></span>|<span data-ttu-id="2e2de-115">제공되는 사용 권한</span><span class="sxs-lookup"><span data-stu-id="2e2de-115">To give permission to</span></span>|  
|----------------------|---------------------------|  
|<span data-ttu-id="2e2de-116">폴더 보기</span><span class="sxs-lookup"><span data-stu-id="2e2de-116">View folders</span></span>|<span data-ttu-id="2e2de-117">폴더 계층과 폴더가 생성 및 수정된 시기를 나타내는 읽기 전용 속성을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-117">View the folder hierarchy and read-only properties that indicate when the folder was created and modified.</span></span><br /><br /> <span data-ttu-id="2e2de-118">사용자가 "보고서 보기", "모델 보기", "리소스 보기" 및 "데이터 원본 보기"가 포함되는 역할에 할당되지 않으면 폴더의 항목을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-118">Users cannot view items in the folder unless they are assigned to roles that also include the following tasks: "View reports," "View models", "View resources," and "View data sources."</span></span>|  
|<span data-ttu-id="2e2de-119">폴더 관리</span><span class="sxs-lookup"><span data-stu-id="2e2de-119">Manage folders</span></span>|<span data-ttu-id="2e2de-120">폴더 속성을 보거나, 이름 또는 설명을 변경하거나, 폴더를 다른 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-120">View folder properties, change the name or description, or move the folder to another location.</span></span> <span data-ttu-id="2e2de-121">이 태스크를 지정하면 사용자가 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-121">This task allows users to create folders.</span></span>|  
|<span data-ttu-id="2e2de-122">보고서 관리</span><span class="sxs-lookup"><span data-stu-id="2e2de-122">Manage reports</span></span>|<span data-ttu-id="2e2de-123">파일 시스템의 보고서를 폴더에 추가하고, 보고서 디자이너의 보고서를 보고서 서버에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-123">Add reports from the file system to a folder and publish reports from Report Designer to the report server.</span></span>|  
|<span data-ttu-id="2e2de-124">데이터 원본 관리</span><span class="sxs-lookup"><span data-stu-id="2e2de-124">Manage data sources</span></span>|<span data-ttu-id="2e2de-125">폴더에 새 공유 데이터 원본 항목을 추가하거나 기존 공유 데이터 원본을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-125">Add new shared data source items to a folder and change existing shared data sources.</span></span>|  
|<span data-ttu-id="2e2de-126">항목의 보안 설정</span><span class="sxs-lookup"><span data-stu-id="2e2de-126">Set security on items</span></span>|<span data-ttu-id="2e2de-127">폴더에 대한 액세스를 제어하는 역할 할당을 생성 및 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-127">Create and modify role assignments that control access to the folder.</span></span> <span data-ttu-id="2e2de-128">이 태스크는 "폴더 보기"나 "폴더 관리"와 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-128">This task must be used with either "View folders" or "Manage folders."</span></span> <span data-ttu-id="2e2de-129">그렇지 않으면 사용자가 항목을 선택할 수 없게 되므로 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2de-129">If it is not, it will have no effect because the user will not be able to select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e2de-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e2de-130">See Also</span></span>  
 <span data-ttu-id="2e2de-131">[보고서 및 리소스 보안](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="2e2de-131">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="2e2de-132">[공유 데이터 원본 항목 보안](secure-shared-data-source-items.md) </span><span class="sxs-lookup"><span data-stu-id="2e2de-132">[Secure Shared Data Source Items](secure-shared-data-source-items.md) </span></span>  
 [<span data-ttu-id="2e2de-133">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="2e2de-133">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
