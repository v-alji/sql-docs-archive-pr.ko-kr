---
title: 서버 관리자 권한 부여 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
author: minewiskan
ms.author: owend
ms.openlocfilehash: 822227ae89f4f219a055bcc0d6d6b0a228f7964b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732191"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a><span data-ttu-id="45f98-102">서버 관리자 권한 부여(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="45f98-102">Grant Server Administrator Permissions (Analysis Services)</span></span>
  <span data-ttu-id="45f98-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 내에서 서버 관리자 역할의 멤버는 해당 인스턴스의 모든 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체와 데이터에 무제한으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-103">Members of the Server administrator role within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] have unrestricted access to all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects and data in that instance.</span></span> <span data-ttu-id="45f98-104">데이터베이스 작성 또는 처리, 서버 속성 수정, 추적 시작(이벤트 처리용 제외) 등의 서버 차원의 태스크를 수행하려면 사용자가 서버 관리자 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-104">A user must be a member of the Server administrator role to perform any server-wide task, such as creating or processing a database, modifying server properties, or launching a trace (other than for processing events).</span></span>

 <span data-ttu-id="45f98-105">역할 멤버 자격은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 이 설치될 때 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-105">Role membership is established when [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is installed.</span></span> <span data-ttu-id="45f98-106">설치 프로그램을 실행하는 사용자는 서버를 제공할 때 본인을 역할에 추가하거나 다른 사용자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-106">The user running the Setup program can add him or herself to the role, or add another user, when provisioning the server.</span></span> <span data-ttu-id="45f98-107">다음 절차를 사용하여 사후 설치 태스크로 역할 멤버 자격을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-107">You can modify role membership as a post-installation task using the following procedure.</span></span>

## <a name="modify-server-role-membership"></a><span data-ttu-id="45f98-108">서버 역할 멤버 자격 수정</span><span class="sxs-lookup"><span data-stu-id="45f98-108">Modify Server Role Membership</span></span>

1.  <span data-ttu-id="45f98-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하고 개체 탐색기에서 인스턴스 이름을 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and then right-click the instance name in Object Explorer and then click **Properties**.</span></span>

2.  <span data-ttu-id="45f98-110">**페이지 선택** 창에서 **보안** 을 클릭하고 페이지 맨 아래쪽에서 **추가** 를 클릭하여 서버 역할에 Windows 사용자나 그룹을 하나 이상 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-110">Click **Security** in the **Select a Page** pane, and then click **Add** at the bottom of the page to add one or more Windows users or groups to the server role.</span></span>

     <span data-ttu-id="45f98-111">![Management Studio에서 사용자 대화 상자 추가](../media/ssas-serveradminadd.png "Management Studio에서 사용자 대화 상자 추가")</span><span class="sxs-lookup"><span data-stu-id="45f98-111">![Add users dialog box in management studio](../media/ssas-serveradminadd.png "Add users dialog box in management studio")</span></span>

 <span data-ttu-id="45f98-112">설치 시 SQL Server 설치 프로그램에서는 적어도 하나 이상의 사용자 계정을 Analysis Services 시스템 관리자로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-112">At installation time, SQL Server Setup requires that you specify at least one user account as the Analysis Services system administrator.</span></span>

 <span data-ttu-id="45f98-113">기본적으로 로컬 관리자 그룹의 멤버는 Analysis Server에서 관리 권한도 부여 받습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-113">By default, members of the local Administrators group are also granted administrative rights in Analysis Server.</span></span> <span data-ttu-id="45f98-114">로컬 그룹은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버 관리자 역할의 멤버 자격을 명시적으로 부여 받지는 않지만 로컬 관리자는 데이터베이스를 만들고 사용자 및 사용 권한을 추가하고 시스템 관리자에게 허용된 기타 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-114">Although the local group is not explicitly granted membership in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server administrator role, local administrators can create databases, add users and permissions, and perform any other task allowed to system administrators.</span></span> <span data-ttu-id="45f98-115">이 동작은 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-115">This behavior is configurable.</span></span> <span data-ttu-id="45f98-116">이 `BuiltinAdminsAreServerAdmins` 속성은 기본적으로 **true** 로 설정 된 서버 속성에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-116">It is determined by the `BuiltinAdminsAreServerAdmins` server property, which is set to **true** by default.</span></span> <span data-ttu-id="45f98-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-117">You can change this property in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="45f98-118">자세한 내용은 [Security Properties](../server-properties/security-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45f98-118">For more information, see [Security Properties](../server-properties/security-properties.md).</span></span>

 <span data-ttu-id="45f98-119">AMO(Analysis Management Objects)를 사용하여 서버 역할을 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f98-119">You can also manage server roles by using Analysis Management Objects (AMO).</span></span> <span data-ttu-id="45f98-120">자세한 내용은 [AMO&#40;Analysis Management Objects&#41;를 사용하여 개발](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45f98-120">For more information, see [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>

## <a name="see-also"></a><span data-ttu-id="45f98-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45f98-121">See Also</span></span>
 <span data-ttu-id="45f98-122">[&#40;개체 및 작업에 대 한 액세스 권한 부여 Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [보안 역할 &#40;Analysis Services-다차원 데이터&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="45f98-122">[Authorizing access to objects and operations &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [Security Roles  &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span></span>


