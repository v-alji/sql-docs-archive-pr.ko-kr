---
title: 보고서 관리자 |를 사용 하 여 모델 만들기 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report models [Reporting Services], creating
- Report Manager [Reporting Services], model creation
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59ce278a22ec9797b001ca37a0bde576483cf5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735104"
---
# <a name="create-a-model-using-report-manager"></a><span data-ttu-id="05ea5-102">보고서 관리자를 사용하여 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="05ea5-102">Create a Model Using Report Manager</span></span>
  <span data-ttu-id="05ea5-103">보고서 관리자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 또는 Oracle 데이터베이스에서 모델을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-103">You can generate models from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, or an Oracle database using Report Manager.</span></span> <span data-ttu-id="05ea5-104">보고서 모델은 보고서 서버에 게시된 공유 데이터 원본에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-104">Report models are generated from shared data sources that are published on the report server.</span></span> <span data-ttu-id="05ea5-105">공유 데이터 원본이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-105">If you do not already have a shared data source, you must create one.</span></span>  
  
 <span data-ttu-id="05ea5-106">생성되는 보고서 모델은 전적으로 공유 데이터 원본의 스키마를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-106">The report model that you generate is based entirely on the schema of the shared data source.</span></span> <span data-ttu-id="05ea5-107">모델에 포함될 데이터 원본 부분을 선택하거나 생성되는 모델의 규칙 또는 메타데이터를 편집할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-107">You cannot choose which parts of the data source are included in the model, nor can you edit the rules or metadata of a generated model.</span></span> <span data-ttu-id="05ea5-108">그러나 모델이 생성된 후 속성을 설정하고 모델 전체 또는 일부에 대한 액세스를 제한하는 역할 할당을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-108">However, you can set properties on the model after it is generated and define role assignments that restrict access to all or part of the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05ea5-109">보고서 관리자 또는 2007를 사용 하 여 생성 된 Oracle 기반 모델에는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[offSPServ](../includes/offspserv-md.md)] [!INCLUDE[SPS2010](../includes/sps2010-md.md)] oracle 데이터 원본에 연결 하는 데 사용 되는 사용자 계정에 대 한 스키마의 일부인 데이터베이스 개체가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-109">An Oracle-based model generated using Report Manager or [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 [!INCLUDE[SPS2010](../includes/sps2010-md.md)] will include database objects that are a part of the schema for the user account used to connect to the Oracle data source.</span></span> <span data-ttu-id="05ea5-110">사용자 계정 이름은 데이터 원본 속성 자격 증명에 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-110">The user account name is specified in the data source properties credentials.</span></span>  
  
### <a name="to-create-a-new-data-source-for-a-report-model-using-report-manager"></a><span data-ttu-id="05ea5-111">보고서 관리자를 사용하여 보고서 모델에 대한 새 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="05ea5-111">To create a new data source for a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="05ea5-112">웹 브라우저의 주소 표시줄에 보고서 서버의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-112">In your Web browser, type the URL for your report server in the address bar.</span></span>  
  
2.  <span data-ttu-id="05ea5-113">**새 데이터 원본**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-113">Click **New Data Source**.</span></span>  
  
3.  <span data-ttu-id="05ea5-114">**이름** 입력란에 데이터 원본의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-114">In the **Name** box, enter a name for the data source.</span></span>  
  
4.  <span data-ttu-id="05ea5-115">필요에 따라 **설명** 입력란에 모델에 대한 간략한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-115">Optionally, enter a brief description of the mode in the **Description** text box.</span></span>  
  
5.  <span data-ttu-id="05ea5-116">**이 데이터 원본 사용** 확인란이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-116">Verify that the **Enable this data source** check box is selected.</span></span>  
  
6.  <span data-ttu-id="05ea5-117">**연결 유형** 목록에서 연결할 데이터 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-117">In the **Connection type** list, select the data source type to which you want to connect.</span></span> <span data-ttu-id="05ea5-118">연결 유형은 **Oracle**, **Microsoft SQL Server** 또는 **Microsoft SQL Server Analysis Services**중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-118">The connection type must be one of the following: **Oracle**, **Microsoft SQL Server** or **Microsoft SQL Server Analysis Services**.</span></span>  
  
7.  <span data-ttu-id="05ea5-119">**연결 문자열** 입력란에 데이터베이스를 가리키는 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-119">In the **Connection string** box, enter the connection string that points to the database.</span></span>  
  
8.  <span data-ttu-id="05ea5-120">보고서 작성기 사용자가 데이터베이스에 연결할 때 사용할 연결 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-120">Select the connection method that Report Builder users will need to use to connect to the database.</span></span>  
  
    -   <span data-ttu-id="05ea5-121">Windows 인증: 운영 체제에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 사용자를 인증하게 하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-121">Windows Authentication: Select this option when you want the operating system to authenticate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] users.</span></span> <span data-ttu-id="05ea5-122">이 옵션을 사용하면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 암호 암호화 같은 Windows 보안 기능을 사용하여 사용자를 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-122">This option allows [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use Windows security features, such as password encryption, to authenticate users.</span></span> <span data-ttu-id="05ea5-123">이 옵션을 반드시 선택하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-123">It is strongly recommended that you select this option.</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="05ea5-124">인증: 사용자가 만든 로그인 계정을 사용할 수 있도록 하려면이 옵션을 선택 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-124">Authentication: Select this option when you want users to use a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account that you created.</span></span> <span data-ttu-id="05ea5-125">사용자는 유효한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인 이름과 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-125">Users must supply a valid [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login name and password.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="05ea5-126">가능하면 Windows 인증을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="05ea5-126">Whenever possible, use Windows Authentication.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-create-a-report-model-using-report-manager"></a><span data-ttu-id="05ea5-127">보고서 관리자를 사용하여 보고서 모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="05ea5-127">To create a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="05ea5-128">보고서 관리자에서 모델에 사용할 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-128">In Report Manager, select the data source that you want to use for your model.</span></span>  
  
     <span data-ttu-id="05ea5-129">속성 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-129">The Properties page is displayed.</span></span>  
  
2.  <span data-ttu-id="05ea5-130">데이터 원본에 대해 지정된 옵션을 사용할 것인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-130">Verify that you want to use the options specified for the data source.</span></span>  
  
3.  <span data-ttu-id="05ea5-131">**모델 생성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-131">Click **Generate Model**.</span></span>  
  
     <span data-ttu-id="05ea5-132">데이터 원본에 대한 일반 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-132">The General page is displayed for the data source.</span></span>  
  
4.  <span data-ttu-id="05ea5-133">**이름** 입력란에 보고서 모델의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-133">In the **Name** box, enter a name for the report model.</span></span>  
  
5.  <span data-ttu-id="05ea5-134">**설명** 입력란에 모델에 대한 간단한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-134">In the **Description** box, enter a brief description of the model.</span></span>  
  
6.  <span data-ttu-id="05ea5-135">보고서 모델을 저장할 새 위치를 지정하려면 **위치 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-135">To specify a new location to save the report model to, click **Change Location**.</span></span>  
  
     <span data-ttu-id="05ea5-136">기본적으로 보고서 모델은 보고서 관리자 홈에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-136">By default, the report model is saved to Report Manager Home.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="05ea5-137">보고서 모델이 생성되고 사용자가 지정한 위치에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-137">The report model is created and saved to the location that you specified.</span></span> <span data-ttu-id="05ea5-138">보고서 관리자를 사용하여 이 모델에 대한 사용 권한을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ea5-138">You can assign permissions to this model by using Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ea5-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05ea5-139">See Also</span></span>  
 <span data-ttu-id="05ea5-140">[기본 모드 보고서 서버에 대한 사용 권한 부여](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="05ea5-140">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="05ea5-141">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="05ea5-141">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="05ea5-142">새 데이터 원본 페이지&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="05ea5-142">New Data Source Page &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/new-data-source-page-report-manager.md)  
  
  
