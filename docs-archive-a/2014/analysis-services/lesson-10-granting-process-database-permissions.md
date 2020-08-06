---
title: 프로세스 데이터베이스 권한 부여 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6ada30e3fb509bd1ffd210485ce0e34b7bf86fb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639052"
---
# <a name="granting-process-database-permissions"></a><span data-ttu-id="41f0c-102">데이터베이스 처리 권한 부여</span><span class="sxs-lookup"><span data-stu-id="41f0c-102">Granting Process Database Permissions</span></span>
  <span data-ttu-id="41f0c-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 설치하면 해당 인스턴스에 있는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버 관리자 역할의 모든 멤버가 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스 내에서 모든 태스크를 수행할 수 있는 서버 차원의 사용 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-103">After you install an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], all members of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server administrator role in that instance have server-wide permissions to perform any task within the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="41f0c-104">기본적으로 어떠한 사용자에게도 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스의 개체를 관리하거나 볼 수 있는 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-104">By default, no other users have any permission to administer or view any objects in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

 <span data-ttu-id="41f0c-105">서버 관리자 역할의 멤버는 사용자를 역할 멤버로 만들어 사용자에게 서버 차원에서 관리자 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-105">A member of the server administrator role can grant users administrative access on a server-wide basis by making them members of the role.</span></span> <span data-ttu-id="41f0c-106">서버 관리자 역할의 멤버는 데이터베이스 수준에서 사용자에게 제한되거나 완전한 관리 또는 액세스 권한을 부여하여 더욱 제한적인 방식으로 액세스 권한을 부여할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-106">A member of the server administrator role can also grant users access on a more limited basis by granting them limited or complete administrative or access permissions at the database level.</span></span> <span data-ttu-id="41f0c-107">제한된 관리자 권한에는 데이터베이스, 큐브 또는 차원 수준의 정의 처리 또는 읽기 권한이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-107">Limited administrative permissions include process or read definition permissions at the database, cube, or dimension level.</span></span>

 <span data-ttu-id="41f0c-108">이 항목의 태스크에서는 역할의 멤버에게 모든 데이터베이스 개체를 처리할 권한은 부여하지만 데이터베이스 내 데이터를 볼 수 있는 권한은 부여하지 않는 데이터베이스 개체 처리 보안 역할을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-108">In the tasks in this topic, you will define a Process Database Objects security role that grants members of the role permission to process all database objects, but no permission to view data within the database.</span></span>

## <a name="defining-a-process-database-objects-security-role"></a><span data-ttu-id="41f0c-109">데이터베이스 개체 처리 보안 역할 정의</span><span class="sxs-lookup"><span data-stu-id="41f0c-109">Defining a Process Database Objects Security Role</span></span>

1.  <span data-ttu-id="41f0c-110">솔루션 탐색기에서 **역할** 을 마우스 오른쪽 단추로 클릭한 다음 **새 역할** 을 클릭하여 역할 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-110">In Solution Explorer, right-click **Roles** and then click **New Role** to open the Role Designer.</span></span>

2.  <span data-ttu-id="41f0c-111">**데이터베이스 처리** 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-111">Click the **Process database** check box.</span></span>

3.  <span data-ttu-id="41f0c-112">속성 창에서이 새 역할에 대 한 **이름** 속성을로 변경 `Process Database Objects Role` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-112">In the Properties window, change the **Name** property for this new role to `Process Database Objects Role`.</span></span>

     <span data-ttu-id="41f0c-113">![역할 디자이너](../../2014/tutorials/media/l10-security-1.png "역할 디자이너")</span><span class="sxs-lookup"><span data-stu-id="41f0c-113">![Role Designer](../../2014/tutorials/media/l10-security-1.png "Role Designer")</span></span>

4.  <span data-ttu-id="41f0c-114">역할 디자이너의 **멤버 자격** 탭으로 전환하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-114">Switch to the **Membership** tab of Role Designer and click **Add**.</span></span>

5.  <span data-ttu-id="41f0c-115">이 역할의 멤버가 될 Windows 도메인 사용자 또는 그룹의 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-115">Enter the accounts of the Windows domain users or groups who will be members of this role.</span></span> <span data-ttu-id="41f0c-116">**이름 확인** 을 클릭하여 계정 정보를 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-116">Click **Check Names** to verify the account information, and then click **OK**.</span></span>

6.  <span data-ttu-id="41f0c-117">역할 디자이너의 **큐브** 탭으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-117">Switch to the **Cubes** tab of Role Designer.</span></span>

     <span data-ttu-id="41f0c-118">이 역할의 멤버에게는 이 데이터베이스를 처리할 권한이 있지만 다음 그림에 표시된 것처럼 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브의 데이터에 액세스할 수 있는 권한과 로컬 큐브/드릴스루 액세스는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-118">Notice that members of this role have permissions to process this database, but have no permission to access the data in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube and have no local cube/drillthrough access, as shown in the following image.</span></span>

     <span data-ttu-id="41f0c-119">![역할 디자이너의 큐브 탭](../../2014/tutorials/media/l10-security-2.png "역할 디자이너의 큐브 탭")</span><span class="sxs-lookup"><span data-stu-id="41f0c-119">![Cubes tab of Role Designer](../../2014/tutorials/media/l10-security-2.png "Cubes tab of Role Designer")</span></span>

7.  <span data-ttu-id="41f0c-120">역할 디자이너의 **차원** 탭으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-120">Switch to the **Dimensions** tab of Role Designer.</span></span>

     <span data-ttu-id="41f0c-121">이 역할의 멤버에게는 이 데이터베이스의 모든 차원 개체를 처리할 수 있는 권한이 있으며 기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 데이터베이스의 각 차원 개체에 액세스하기 위한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-121">Notice that members of this role have permissions to process all dimension objects in this database, and, by default, have read permissions to access each dimension object in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial database.</span></span>

8.  <span data-ttu-id="41f0c-122">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-122">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

     <span data-ttu-id="41f0c-123">이제 데이터베이스 개체 처리 보안 역할을 성공적으로 정의하여 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-123">You have now successfully defined and deployed the Process Database Objects security role.</span></span> <span data-ttu-id="41f0c-124">큐브가 프로덕션 환경으로 배포된 후에 배포된 큐브의 관리자는 필요에 따라 이 역할에 사용자를 추가하여 특정 사용자에게 처리 권한을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-124">After a cube is deployed to the production environment, the administrators of the deployed cube can add users to this role as required to delegate processing responsibilities to specific users.</span></span>

> [!NOTE]
>  <span data-ttu-id="41f0c-125">10단원의 완료된 프로젝트는 예제를 다운로드 및 설치하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41f0c-125">A completed project for Lesson 10 is available by downloading and installing the samples.</span></span> <span data-ttu-id="41f0c-126">자세한 내용은 [Analysis Services 다차원 모델링 자습서에 대 한 샘플 데이터 및 프로젝트 설치](install-sample-data-and-projects.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41f0c-126">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41f0c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41f0c-127">See Also</span></span>
 [<span data-ttu-id="41f0c-128">역할 및 권한&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="41f0c-128">Roles and Permissions &#40;Analysis Services&#41;</span></span>](multidimensional-models/roles-and-permissions-analysis-services.md)


