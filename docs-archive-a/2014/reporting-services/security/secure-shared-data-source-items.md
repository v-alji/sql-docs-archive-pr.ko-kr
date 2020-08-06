---
title: 공유 데이터 원본 항목 보안 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
- security [Reporting Services], data sources
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4177834a90e2852f4079e3b2bf5a1dd85b9cd51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651469"
---
# <a name="secure-shared-data-source-items"></a><span data-ttu-id="1e162-102">공유 데이터 원본 항목 보안 설정</span><span class="sxs-lookup"><span data-stu-id="1e162-102">Secure Shared Data Source Items</span></span>
  <span data-ttu-id="1e162-103">공유 데이터 원본 항목에 대한 보안을 설정하여 해당 항목에 대한 액세스를 허용하거나 허용하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-103">You can set security on a shared data source item to enable or disable access to it.</span></span>  
  
 <span data-ttu-id="1e162-104">사용자가 보고서 자체를 볼 수 있도록 인증된 경우 공유 데이터 원본에 대해 최소 액세스 권한(예: **브라우저** 역할을 통해서 허용되는 액세스)이 있는 사용자는 해당 항목을 사용하는 보고서 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-104">A user who has minimal access to a shared data source (for example, the access granted through the **Browser** role) can view the list of reports that use the item, provided the user is also authorized to view the reports themselves.</span></span>  
  
 <span data-ttu-id="1e162-105">추가 액세스 권한(예: **내용 관리자** 역할을 통해서 허용되는 액세스)이 있는 사용자는 공유 데이터 원본에 대한 속성을 보거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-105">A user who has additional access (such as that granted through the **Content Manager** role) can view and set properties for the shared data source.</span></span>  
  
 <span data-ttu-id="1e162-106">보안을 설정하려면 공유 데이터 원본에 대한 액세스 권한이 있는 사용자 또는 그룹 계정을 지정하는 역할 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-106">To set security, you create a role assignment that specifies which user or group account has access to the shared data source.</span></span> <span data-ttu-id="1e162-107">공유 데이터 원본 항목에 대한 액세스 권한이 있는 사용자는 해당 항목의 이름, 설명, 연결 문자열 또는 자격 증명 정보를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-107">Users who have access to a shared data source item can change its name, description, connection string, or credential information.</span></span>  
  
## <a name="tasks-and-access-to-items"></a><span data-ttu-id="1e162-108">태스크 및 항목 액세스</span><span class="sxs-lookup"><span data-stu-id="1e162-108">Tasks and Access to Items</span></span>  
 <span data-ttu-id="1e162-109">역할 할당을 만들 때 이러한 태스크가 포함된 역할을 사용하여 사용자 및 그룹에 적절한 사용 권한을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-109">When creating role assignments, use a role that has these tasks to assign appropriate permissions to users and groups.</span></span>  
  
|<span data-ttu-id="1e162-110">태스크 선택</span><span class="sxs-lookup"><span data-stu-id="1e162-110">Select this task</span></span>|<span data-ttu-id="1e162-111">사용자에게 제공되는 사용 권한</span><span class="sxs-lookup"><span data-stu-id="1e162-111">To give users permission to</span></span>|  
|----------------------|---------------------------------|  
|<span data-ttu-id="1e162-112">데이터 원본 보기</span><span class="sxs-lookup"><span data-stu-id="1e162-112">View data sources</span></span>|<span data-ttu-id="1e162-113">폴더 계층에 있는 공유 데이터 원본 항목을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-113">View the shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="1e162-114">이 태스크가 없으면 항목이 사용자에게 표시되지 않으므로 데이터 원본이 사용 가능한지 여부를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-114">Without this task, the item is not visible to users and they may not be aware that the data source is available.</span></span>|  
|<span data-ttu-id="1e162-115">데이터 원본 관리</span><span class="sxs-lookup"><span data-stu-id="1e162-115">Manage data sources</span></span>|<span data-ttu-id="1e162-116">이름, 설명 및 연결 정보를 지정하는 속성을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-116">View properties that specify the name, description, and connection information.</span></span> <span data-ttu-id="1e162-117">이 태스크는 폴더 계층에 공유 데이터 원본 항목을 표시하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-117">This task is also used to display a shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="1e162-118">이 태스크를 선택하면 "데이터 원본 보기" 작업을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-118">If you choose this task, you can omit the "View data sources" task.</span></span>|  
|<span data-ttu-id="1e162-119">항목의 보안 설정</span><span class="sxs-lookup"><span data-stu-id="1e162-119">Set security on items</span></span>|<span data-ttu-id="1e162-120">공유 데이터 원본에 대한 액세스를 제어하는 역할 할당을 만들고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-120">Create and modify role assignments that control access to the shared data source.</span></span> <span data-ttu-id="1e162-121">이 태스크는 "데이터 원본 보기" 또는 "데이터 원본 관리" 작업과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-121">This task must be used with either "View data source" or "Manage data sources" tasks.</span></span> <span data-ttu-id="1e162-122">그렇지 않으면 사용자가 항목을 선택할 수 없으므로 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e162-122">If it is not, it has no effect because the user cannot select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e162-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e162-123">See Also</span></span>  
 <span data-ttu-id="1e162-124">[보고서 데이터 원본 관리](../report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="1e162-124">[Manage Report Data Sources](../report-data/manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="1e162-125">[보안 폴더](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="1e162-125">[Secure Folders](secure-folders.md) </span></span>  
 <span data-ttu-id="1e162-126">[보고서 및 리소스 보안](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="1e162-126">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="1e162-127">[기본 모드 보고서 서버에 대한 사용 권한 부여](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="1e162-127">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="1e162-128">Reporting Services 데이터 원본에 자격 증명 저장</span><span class="sxs-lookup"><span data-stu-id="1e162-128">Store Credentials in a Reporting Services Data Source</span></span>](../report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
  
