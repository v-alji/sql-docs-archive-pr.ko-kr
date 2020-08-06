---
title: 서버 구성 유틸리티 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f985338e44bf0f4b591fcb70a4e093901626149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743511"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a><span data-ttu-id="c92bc-102">서버 구성 유틸리티(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="c92bc-102">Server Configuration Utility (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="c92bc-103">Excel 용 데이터 마이닝 추가 기능을 설치 하면 서버 구성 유틸리티도 설치 되며 추가 기능을 처음 열 때 실행 됩니다. 이 항목에서는 유틸리티를 사용 하 여 인스턴스에 연결 하 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 고 데이터 마이닝 모델을 사용 하기 위해 데이터베이스를 설정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-103">When you install the Data Mining Add-ins for Excel, a Server Configuration Utility is also installed, and will run the first time you open the add-ins. This topic describes how to use the utility to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and set up a database for working with data mining models.</span></span>  
  

  
##  <a name="step-1-connect-to-analysis-services"></a><a name="bkmk_step1"></a><span data-ttu-id="c92bc-104">1 단계: Analysis Services에 연결</span><span class="sxs-lookup"><span data-stu-id="c92bc-104">Step 1: Connect to Analysis Services</span></span>  
 <span data-ttu-id="c92bc-105">데이터 마이닝 알고리즘을 제공하고 사용자의 데이터 마이닝 모델을 저장하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-105">Choose the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that provides the data mining algorithms and stores your data mining models.</span></span>  
  
 <span data-ttu-id="c92bc-106">데이터 마이닝을 설정하기 위한 연결을 만들 때는 데이터 마이닝 모델을 실험할 수 있는 서버를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-106">When you create a connection to enable data mining, you should choose a server where you can experiment with data mining models.</span></span> <span data-ttu-id="c92bc-107">서버에서 새 데이터베이스를 만들고 이를 데이터 마이닝 전용으로 사용하거나 관리자에게 데이터 마이닝 서버를 준비하도록 요청하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-107">We recommend that you create a new database on the server and dedicate the new database to data mining, or ask your administrator to prepare a data mining server for you.</span></span> <span data-ttu-id="c92bc-108">이렇게 하면 다른 서비스의 성능에 영향을 주지 않고 모델을 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-108">That way you can build models without affecting the performance of other services.</span></span>  
  
 <span data-ttu-id="c92bc-109">데이터 마이닝에 사용하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버는 원본 데이터와 동일한 서버에 있을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-109">Note that the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that you use for data mining does not need to be on the same server as your source data.</span></span>  
  
 <span data-ttu-id="c92bc-110">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="c92bc-110">**Server name**</span></span>  
 <span data-ttu-id="c92bc-111">데이터 마이닝에 사용할 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스가 포함된 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-111">Type the name of the server that contains the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you will use for data mining.</span></span>  
  
 <span data-ttu-id="c92bc-112">**인증**</span><span class="sxs-lookup"><span data-stu-id="c92bc-112">**Authentication**</span></span>  
 <span data-ttu-id="c92bc-113">인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-113">Specify the authentication methods.</span></span> <span data-ttu-id="c92bc-114">관리자가 HTTPPump를 통해 서버에 액세스하도록 구성하지 않은 한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 연결하려면 Windows 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-114">Windows Authentication is required for connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], unless your administrator has configured access to the server via the HTTPPump.</span></span>  
  
##  <a name="step-2-allow-temporary-models"></a><a name="bkmk_step2"></a><span data-ttu-id="c92bc-115">2 단계: 임시 모델 허용</span><span class="sxs-lookup"><span data-stu-id="c92bc-115">Step 2: Allow Temporary Models</span></span>  
 <span data-ttu-id="c92bc-116">추가 기능을 사용하려면 먼저 임시 마이닝 모델 생성을 허용하도록 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버 속성을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-116">Before you can use the add-ins, an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server property must be changed to permit the creation of temporary mining models.</span></span>  
  
 <span data-ttu-id="c92bc-117">임시 마이닝 모델은 *세션 모델*이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-117">Temporary mining models are also called *session models*.</span></span> <span data-ttu-id="c92bc-118">현재 세션이 열려 있는 동안에만 모델이 저장되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-118">This is because the models are stored only as long as your current session is open.</span></span> <span data-ttu-id="c92bc-119">서버에 대한 연결을 닫으면 세션이 종료되고 세션이 열려 있는 동안 사용된 모든 모델이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-119">When you close your connection to the server, the session is ended and any models used during the session are deleted.</span></span>  
  
 <span data-ttu-id="c92bc-120">세션 마이닝 모델을 사용하더라도 서버의 스토리지 공간에는 영향이 없지만 데이터 마이닝 모델을 만드는 데 따르는 오버헤드가 서버 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-120">The use of session mining models does not affect storage space on the server, but the overhead involved in creating data mining models may affect the performance of the server.</span></span>  
  
 <span data-ttu-id="c92bc-121">마법사는 먼저 사용자가 지정한 서버에서 설정을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-121">The wizard first detects the settings on the server that you specified.</span></span> <span data-ttu-id="c92bc-122">서버에서 이미 임시 마이닝 모델을 허용 하는 경우 **다음** 을 클릭 하 여 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-122">If the server already allows temporary mining models, you can click **Next** to continue.</span></span> <span data-ttu-id="c92bc-123">마법사에는 또한 지정된 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에서 임시 마이닝 모델을 사용하도록 설정하는 방법 또는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 관리자에게 요청을 수행하는 방법에 대한 지침이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-123">The wizard also provides instructions for how to enable temporary mining models on the specified [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, or how to make a request to your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] administrator.</span></span>  
  
##  <a name="step-3-create-database-for-add-in-users"></a><a name="bkmk_step3"></a><span data-ttu-id="c92bc-124">3 단계: 추가 기능 사용자를 위한 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="c92bc-124">Step 3: Create Database for Add-in Users</span></span>  
 <span data-ttu-id="c92bc-125">설정 및 구성 마법사의 이 페이지에서 데이터 마이닝 전용의 새 데이터베이스를 만들거나 기존 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-125">On this page of the setup and configuration wizard, you can create a new database that is dedicated to data mining, or select an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c92bc-126">데이터 마이닝을 위해서는 다차원 모드로 실행 중인 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-126">Data mining requires an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that is running in multidimensional mode.</span></span> <span data-ttu-id="c92bc-127">테이블 형식 모드에서는 데이터 마이닝이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-127">Tabular mode does not support data mining.</span></span>  
  
 <span data-ttu-id="c92bc-128">데이터 마이닝 전용의 별도의 데이터베이스를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-128">We recommend that you create a separate database dedicated to data mining.</span></span> <span data-ttu-id="c92bc-129">이렇게 하면 다른 솔루션 개체에 영향을 주지 않고 데이터 마이닝 모델을 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-129">This lets you experiment with data mining models without affecting other solution objects.</span></span>  
  
 <span data-ttu-id="c92bc-130">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 기존 데이터베이스를 선택할 경우에는, 추가 기능을 사용해서 모델을 만들 때 해당 이름의 모델이 이미 있으면 기존 모델을 덮어쓸 수 있으므로 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-130">If you choose an existing database on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], note that it is possible to overwrite existing models if you use the add-ins to create a model and a model of that name already exists.</span></span>  
  
 <span data-ttu-id="c92bc-131">**새 데이터베이스 만들기**</span><span class="sxs-lookup"><span data-stu-id="c92bc-131">**Create new database**</span></span>  
 <span data-ttu-id="c92bc-132">선택한 서버에 새 데이터베이스를 만들려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-132">Select this option to create a new database on the selected server.</span></span> <span data-ttu-id="c92bc-133">데이터 마이닝 데이터베이스에는 데이터 원본, 마이닝 구조 및 마이닝 모델이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-133">A data mining database will store your data sources, mining structures, and mining models.</span></span>  
  
 <span data-ttu-id="c92bc-134">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="c92bc-134">**Database name**</span></span>  
 <span data-ttu-id="c92bc-135">새 데이터베이스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-135">Type the name of the new database.</span></span> <span data-ttu-id="c92bc-136">이름이 사용 중이 아니면 해당 이름으로 데이터베이스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-136">If the name is not already in use, it will be created for you.</span></span>  
  
 <span data-ttu-id="c92bc-137">**기존 데이터베이스 사용**</span><span class="sxs-lookup"><span data-stu-id="c92bc-137">**Use existing database**</span></span>  
 <span data-ttu-id="c92bc-138">기존 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-138">Select this option to use an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="c92bc-139">**Database**</span><span class="sxs-lookup"><span data-stu-id="c92bc-139">**Database**</span></span>  
 <span data-ttu-id="c92bc-140">기존 데이터베이스를 사용하는 옵션을 선택한 경우 목록에서 데이터베이스 이름을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-140">If you chose the option to use an existing database, you must select the database name from the list.</span></span>  
  
##  <a name="step-4-give-add-in-users-appropriate-permissions"></a><a name="bkmk_step4"></a><span data-ttu-id="c92bc-141">4 단계: 추가 기능 사용자에 게 적절 한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="c92bc-141">Step 4: Give Add-in Users Appropriate Permissions</span></span>  
 <span data-ttu-id="c92bc-142">사용자(및 추가 기능의 다른 모든 사용자)에게 데이터 마이닝 구조 및 모델을 탐색, 편집, 처리 또는 생성하는 데 필요한 권한이 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-142">You must ensure that you (and any other users of the add-ins) have the necessary permissions to browse, edit, process, or create data mining structures and models.</span></span>  
  
 <span data-ttu-id="c92bc-143">기본적으로 추가 기능을 사용하려면 통합 Windows 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-143">By default, integrated Windows Authentication is required to use the add-ins.</span></span>  
  
 <span data-ttu-id="c92bc-144">**추가 기능 사용자에게 데이터베이스 관리 권한 부여**</span><span class="sxs-lookup"><span data-stu-id="c92bc-144">**Give add-in users database administration permissions**</span></span>  
 <span data-ttu-id="c92bc-145">나열된 사용자에게 데이터베이스에 대한 관리 액세스 권한을 부여하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-145">Select this option to give the listed users administrative access to the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c92bc-146">이러한 권한은 **데이터베이스 이름** 상자에 나열 된 데이터베이스에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-146">These permissions apply only to the database listed in the **Database name** box.</span></span>  
  
 <span data-ttu-id="c92bc-147">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="c92bc-147">**Database name**</span></span>  
 <span data-ttu-id="c92bc-148">선택한 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-148">Displays the name of the selected database.</span></span>  
  
 <span data-ttu-id="c92bc-149">**추가할 사용자 또는 그룹을 지정합니다.**</span><span class="sxs-lookup"><span data-stu-id="c92bc-149">**Specify users or groups to add**</span></span>  
 <span data-ttu-id="c92bc-150">데이터 마이닝에 사용되는 데이터베이스에 대한 액세스 권한을 가질 로그인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-150">Select the logins that will have access to the database used for data mining.</span></span>  
  
 <span data-ttu-id="c92bc-151">**추가**</span><span class="sxs-lookup"><span data-stu-id="c92bc-151">**Add**</span></span>  
 <span data-ttu-id="c92bc-152">대화 상자를 열어 사용자 또는 그룹을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-152">Click to open a dialog box and add users or groups.</span></span>  
  
 <span data-ttu-id="c92bc-153">**제거**</span><span class="sxs-lookup"><span data-stu-id="c92bc-153">**Remove**</span></span>  
 <span data-ttu-id="c92bc-154">선택한 사용자 또는 그룹을 관리 권한이 있는 사용자 목록에서 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c92bc-154">Click to remove the selected user or group from the list of users with administration permissions.</span></span>  
  
  
