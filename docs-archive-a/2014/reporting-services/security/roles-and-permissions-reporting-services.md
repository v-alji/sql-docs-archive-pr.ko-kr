---
title: 역할 및 권한(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- access controls [Reporting Services]
- permissions [Reporting Services], about permissions
- security [Reporting Services], identity and access control
- authentication [Reporting Services]
- permissions [Reporting Services]
- security [Reporting Services], role-based
- identity [Reporting Services]
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e6098a51afde04164e3ef0dfa5e5297457b4440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651475"
---
# <a name="roles-and-permissions-reporting-services"></a><span data-ttu-id="401de-102">역할 및 권한(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="401de-102">Roles and Permissions (Reporting Services)</span></span>
  <span data-ttu-id="401de-103">Reporting Services는 인증 하위 시스템 및 역할 기반 권한 부여 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="401de-103">Reporting Services provides an authentication subsystem and role-based authorization model.</span></span> <span data-ttu-id="401de-104">인증 및 권한 부여 모델은 보고서 서버가 기본 모드에서 실행되는지, SharePoint 모드에서 실행되는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="401de-104">Authentication and authorization models vary depending on whether the report server runs in native mode or SharePoint mode.</span></span> <span data-ttu-id="401de-105">보고서 서버가 SharePoint 배포에 속하는 경우 SharePoint 권한에 따라 보고서 서버에 액세스할 수 있는 사용자가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="401de-105">If the report server is part of a SharePoint deployment, SharePoint permissions determine who has access to the report server.</span></span>  
  
## <a name="identity-and-access-control-for-native-mode"></a><span data-ttu-id="401de-106">기본 모드에 대한 ID 및 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="401de-106">Identity and Access Control for Native Mode</span></span>  
 <span data-ttu-id="401de-107">기본 인증은 Windows 인증 및 통합 보안을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="401de-107">Default authentication is based on Windows Authentication and integrated security.</span></span> <span data-ttu-id="401de-108">보고서 서버가 여러 인증 요청에 응답할 수 있도록 인증 설정을 변경할 수 있으며, 기본 보안 기능을 사용자가 제공하는 사용자 지정 인증 확장 프로그램으로 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="401de-108">You can change the authentication settings to allow the report server to respond to different authentication requests, or even replace the default security features with a custom authentication extension that you provide.</span></span>  
  
 <span data-ttu-id="401de-109">권한 부여는 사용자가 보안 주체에 할당하는 역할을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="401de-109">Authorization is based on roles that you assign to a principle.</span></span> <span data-ttu-id="401de-110">각 역할은 관련 태스크 집합으로 구성되어 있으며 이러한 태스크는 관련 작업으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="401de-110">Each role consists of a set of related tasks, which are in turn composed of related operations.</span></span> <span data-ttu-id="401de-111">예를 들어 **보고서 관리** 태스크는 보고서 보기, 보고서 추가, 보고서 업데이트, 보고서 삭제, 보고서 예약, 보고서 속성 업데이트와 같은 보고서 서버 작업에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="401de-111">For example, the **Manage reports** task grants access to the following report server operations: view reports, add report, update report, delete report, schedule report, and update report properties.</span></span>  
  
## <a name="identity-and-access-control-for-sharepoint-mode"></a><span data-ttu-id="401de-112">SharePoint 모드에 대한 ID 및 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="401de-112">Identity and Access Control for SharePoint Mode</span></span>  
 <span data-ttu-id="401de-113">SharePoint 통합 모드에서 인증 및 권한 부여는 이러한 요청이 보고서 서버에 도달하기 전에 SharePoint 사이트에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="401de-113">In SharePoint integrated mode, authentication and authorization are handled on the SharePoint site, before requests reach the report server.</span></span> <span data-ttu-id="401de-114">인증 구성 방식에 따라 SharePoint 사이트의 요청에 보안 토큰이나 신뢰할 수 있는 사용자 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="401de-114">Depending on how you configure authentication, requests from a SharePoint site include a security token or a trusted user name.</span></span> <span data-ttu-id="401de-115">SharePoint 사용자 및 그룹에 대해 설정한 사용 권한은 SharePoint 라이브러리에 있는 보고서 서버 항목에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="401de-115">Permissions that you set for SharePoint users and groups authorize access to report server items that are placed in SharePoint libraries.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="401de-116">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="401de-116">In This Section</span></span>  
 [<span data-ttu-id="401de-117">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="401de-117">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
 <span data-ttu-id="401de-118">내용 및 작업에 대한 액세스 권한을 제공하는 역할 기반 권한 부여 모델에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="401de-118">Describes the role-based authorization model that provides access to content and operations.</span></span>  
  
 [<span data-ttu-id="401de-119">SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="401de-119">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 <span data-ttu-id="401de-120">SharePoint 그룹, 사용 권한 수준 및 사용 권한을 사용하여 보고서 서버에 대한 액세스를 제어하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="401de-120">Explains how SharePoint groups, permission levels, and permissions are used to control access to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401de-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="401de-121">See Also</span></span>  
 <span data-ttu-id="401de-122">[보고서 서버 인증](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="401de-122">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 [<span data-ttu-id="401de-123">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="401de-123">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
