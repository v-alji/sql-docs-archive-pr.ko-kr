---
title: 데이터 마이닝 구조 및 모델에 대 한 권한 부여 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.miningmodels.f1
helpviewer_keywords:
- data mining [Analysis Services], security
- permissions [Analysis Services], mining models
- mining models [Analysis Services], security
- mining structures [Analysis Services], security
- permissions [Analysis Services], mining structures
- user access rights [Analysis Services], mining structures
- user access rights [Analysis Services], mining models
ms.assetid: a0008004-e2b7-47db-acad-5fe7e12b130f
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0db849551bdb38615f280b123c98f0e9d3053d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734508"
---
# <a name="grant-permissions-on-data-mining-structures-and-models-analysis-services"></a><span data-ttu-id="2b909-102">데이터 마이닝 구조 및 모델에 대한 권한 부여(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2b909-102">Grant permissions on data mining structures and models (Analysis Services)</span></span>
  <span data-ttu-id="2b909-103">기본적으로 Analysis Services 서버 관리자만 데이터베이스의 데이터 마이닝 구조 또는 마이닝 모델을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-103">By default, only an Analysis Services server administrator has permissions to view data mining structures or mining models in the database.</span></span> <span data-ttu-id="2b909-104">관리자가 아닌 사용자에게 권한을 부여하려면 아래 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="2b909-104">Follow the instructions below to grant permissions to non-administrator users.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-structure"></a><span data-ttu-id="2b909-105">마이닝 구조에 대한 액세스 권한 설정</span><span class="sxs-lookup"><span data-stu-id="2b909-105">Set permissions to access a mining structure</span></span>  
  
1.  <span data-ttu-id="2b909-106">SSMS에서 Analysis Services에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-106">In SSMS, connect to Analysis Services.</span></span> <span data-ttu-id="2b909-107">단계에서 도움이 필요한 경우 [클라이언트 애플리케이션에서 연결&#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b909-107">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with the steps.</span></span>  
  
2.  <span data-ttu-id="2b909-108">**데이터베이스** 폴더를 열고 개체 탐색기에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-108">Open the **Databases** folder, and select a database in Object Explorer.</span></span>  
  
3.  <span data-ttu-id="2b909-109">**역할** 을 마우스 오른쪽 단추로 클릭하고 **새 역할**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-109">Right-click **Roles** and choose **New Role**.</span></span>  
  
4.  <span data-ttu-id="2b909-110">일반 페이지에서 이름 및 설명(옵션)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-110">In the General page, enter a name, and optionally, a description.</span></span> <span data-ttu-id="2b909-111">또한 이 페이지는 모든 권한, 데이터베이스 처리, 정의 읽기 등의 몇 가지 데이터베이스 권한을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-111">The page also contains several database permissions, such as Full Control, Process Database, and Read Definition.</span></span> <span data-ttu-id="2b909-112">데이터 마이닝 액세스에는 이러한 권한이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-112">None of these permissions are needed for data mining access.</span></span> <span data-ttu-id="2b909-113">데이터베이스 권한에 대한 자세한 내용은 [데이터베이스 권한 부여&#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b909-113">See [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for more information about database permissions.</span></span>  
  
5.  <span data-ttu-id="2b909-114">**마이닝 구조** 창에서 각 데이터 마이닝 구조에 대해 **읽기** 또는 **읽기/쓰기**  를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-114">In the **Mining Structure** pane, select **Read** or **Read/Write**  for each data mining structure.</span></span>  
  
6.  <span data-ttu-id="2b909-115">**멤버 자격** 창에서 이 역할을 사용하여 Analysis Services에 연결하는 Windows 사용자 및 그룹 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-115">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
7.  <span data-ttu-id="2b909-116">**확인** 을 클릭하여 역할 만들기를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-116">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-model"></a><span data-ttu-id="2b909-117">마이닝 모델에 대한 액세스 권한 설정</span><span class="sxs-lookup"><span data-stu-id="2b909-117">Set permissions to access a mining model</span></span>  
 <span data-ttu-id="2b909-118">데이터 마이닝 모델의 경우 특정 역할에 **읽기** 또는 **읽기/쓰기** 권한뿐 아니라 기본 데이터를 보고 검색할 수 있는 **드릴스루** 및 **정의 읽기** 권한도 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-118">For a data mining model, a role can have either **Read** or **Read/Write** permissions, as well as **Drillthrough** and **Read Definition** permissions that allow viewing and browsing the underlying data.</span></span>  
  
 <span data-ttu-id="2b909-119">**참고** 마이닝 구조와 마이닝 모델 모두에서 드릴스루할 수 있으면 마이닝 모델 및 마이닝 구조에 대해 드릴스루 권한을 가지는 역할의 멤버인 사용자는 마이닝 모델에 열이 포함되지 않은 경우에도 마이닝 구조의 열을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-119">**Note** If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model and the mining structure can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="2b909-120">따라서 중요한 정보를 보호하려면 개인 정보를 마스킹하도록 데이터 원본 뷰를 설정하고 필요한 경우에만 마이닝 구조에 드릴스루 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-120">Therefore, to protect sensitive information, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
 <span data-ttu-id="2b909-121">데이터베이스 역할에 읽기 또는 읽기/쓰기 권한을 부여하려면 사용자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버 역할의 멤버이거나 모든(관리자) 권한을 가진 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-121">To grant read or read/write permissions to a database role, a user must be a member of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server role or a member of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database role that has Full Control (Administrator) permissions.</span></span>  
  
1.  <span data-ttu-id="2b909-122">에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 인스턴스에 연결 하 고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체 탐색기에서 해당 데이터베이스에 대 한 **역할** 을 확장 한 다음 데이터베이스 역할을 클릭 하거나 새 데이터베이스 역할을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="2b909-123">**마이닝 구조** 창의 **마이닝 모델** 목록에서 마이닝 모델을 찾은 다음 해당 마이닝 모델에 대해 **읽기**, **읽기/쓰기**, **드릴스루**또는 **찾아보기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-123">In the **Mining Structure** pane, locate the mining model in the **Mining Models** list, and then select **Read**, **Read/Write**, **Drill Through**, or **Browse** for that mining model.</span></span>  
  
3.  <span data-ttu-id="2b909-124">**멤버 자격** 창에서 이 역할을 사용하여 Analysis Services에 연결하는 Windows 사용자 및 그룹 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-124">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="2b909-125">**확인** 을 클릭하여 역할 만들기를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-125">Click **OK** to finish creating the role.</span></span>  
  
 <span data-ttu-id="2b909-126">DMX(Data Mining Extensions) OPENQUERY 절을 사용하는 드릴스루 쿼리에서 데이터 원본을 사용하려면 데이터베이스 역할이 해당 데이터 원본 개체에 대해 읽기/쓰기 권한도 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-126">To use a data source in a drillthrough query that uses the Data Mining Extensions (DMX) OPENQUERY clause, the database role also needs read/write permission on the appropriate data source object.</span></span> <span data-ttu-id="2b909-127">자세한 내용은 [데이터 원본 개체에 대한 권한 부여&#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) 및 [OPENQUERY&#40;DMX&#41;](/sql/dmx/source-data-query-openquery)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b909-127">For more information, see [Grant permissions on a data source object &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) and [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b909-128">기본적으로 OPENROWSET을 사용하여 DMX 쿼리를 제출하는 기능이 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b909-128">By default, the submission of DMX queries by using OPENROWSET is disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b909-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b909-129">See Also</span></span>  
 <span data-ttu-id="2b909-130">[Analysis Services&#41;&#40;서버 관리자 권한 부여](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="2b909-130">[Grant Server Administrator Permissions &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="2b909-131">[큐브 또는 모델 권한 부여 &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="2b909-131">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 <span data-ttu-id="2b909-132">[차원 데이터 &#40;Analysis Services&#41;에 대 한 사용자 지정 액세스 권한 부여](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="2b909-132">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 [<span data-ttu-id="2b909-133">셀 데이터에 대한 사용자 지정 액세스 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2b909-133">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
