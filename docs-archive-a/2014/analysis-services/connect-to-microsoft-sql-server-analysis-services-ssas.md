---
title: Microsoft SQL Server Analysis Services에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
ms.openlocfilehash: 984979480e3ea54c86c986fa6dd9771aaf879cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647995"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a><span data-ttu-id="b1480-102">Microsoft SQL Server Analysis Services에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="b1480-102">Connect to Microsoft SQL Server Analysis Services (SSAS)</span></span>
  <span data-ttu-id="b1480-103">**테이블 가져오기 마법사** 의이 페이지에서는 SharePoint에서 호스팅되는 PowerPivot 통합 문서나 Microsoft SQL Server Analysis Services 큐브에서 데이터를 가져오기 위한 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-103">This page of the **Table Import Wizard** enables you to specify settings to import data from a Microsoft SQL Server Analysis Services cube or a PowerPivot workbook that is hosted on SharePoint.</span></span> <span data-ttu-id="b1480-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b1480-105">데이터 원본에 연결하려면 컴퓨터에 적절한 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1480-106">이 페이지에서 데이터베이스를 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="b1480-107">하지만 가장 정보 페이지에 지정된 사용자에게 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b1480-108">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b1480-108">UI element list</span></span>  
 <span data-ttu-id="b1480-109">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="b1480-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="b1480-110">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="b1480-111">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-111">This is a required field.</span></span>  
  
 <span data-ttu-id="b1480-112">**서버 또는 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="b1480-112">**Server or File Name**</span></span>  
 <span data-ttu-id="b1480-113">다음 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-113">Enter one of the following:</span></span>  
  
-   <span data-ttu-id="b1480-114">연결할 SQL Server Analysis Services 서버의 이름이나 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-114">Type the name or IP address of the SQL Server Analysis Services server to connect to.</span></span>  
  
     <span data-ttu-id="b1480-115">마침표(.), (local) 또는 localhost를 사용하여 로컬 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-115">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
-   <span data-ttu-id="b1480-116">SharePoint에 게시할 PowerPivot 통합 문서의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-116">Type the URL of a PowerPivot workbook that is published to SharePoint.</span></span>  
  
 <span data-ttu-id="b1480-117">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="b1480-117">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="b1480-118">Windows 인증을 사용하여 SQL Server Analysis Services 서버에 연결할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-118">Specify whether Windows Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="b1480-119">Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-119">Windows Authentication mode enables a user to connect through a Windows user account.</span></span> <span data-ttu-id="b1480-120">가능하면 Windows 인증을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1480-120">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="b1480-121">Windows 인증을 사용하는 경우 현재 사용자의 자격 증명을 사용하여 테이블 속성 창 및 가져오기 마법사에서 데이터를 미리 보거나 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-121">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b1480-122">이러한 자격 증명은 데이터를 가져오거나 새로 고칠 때는 사용되지 않습니다. 이 경우에는 가장 정보 페이지에서 지정한 Windows 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-122">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="b1480-123">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="b1480-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="b1480-124">SQL Server 인증을 사용하여 SQL Server Analysis Services 서버에 연결할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-124">Specify whether SQL Server Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="b1480-125">SQL Server 인증을 사용하는 경우 SQL Server는 SQL Server 로그인 계정이 설정되어 있고 지정한 암호가 이전에 기록한 암호와 일치하는지를 자체적으로 확인하여 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-125">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="b1480-126">SQL Server 인증은 데이터 원본에 대한 연결 문자열을 구성할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-126">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="b1480-127">이러한 자격 증명은 테이블 속성 창과 가져오기 마법사에서 데이터를 미리 보거나 필터링할 때도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-127">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b1480-128">이러한 자격 증명은 데이터를 가져오거나 새로 고칠 때는 사용되지 않습니다. 이 경우에는 가장 정보 페이지에서 지정한 Windows 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-128">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="b1480-129">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="b1480-129">**User name**</span></span>  
 <span data-ttu-id="b1480-130">데이터베이스 연결의 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-130">Specify a user name for the database connection.</span></span> <span data-ttu-id="b1480-131">이 옵션은 Windows 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-131">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="b1480-132">**암호**</span><span class="sxs-lookup"><span data-stu-id="b1480-132">**Password**</span></span>  
 <span data-ttu-id="b1480-133">데이터베이스 연결의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-133">Specify a password for the database connection.</span></span> <span data-ttu-id="b1480-134">이 옵션은 SQL Server 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-134">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b1480-135">**내 암호 저장**</span><span class="sxs-lookup"><span data-stu-id="b1480-135">**Save my password**</span></span>  
 <span data-ttu-id="b1480-136">**암호** 상자에 입력한 암호를 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-136">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="b1480-137">이 옵션은 SQL Server 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-137">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b1480-138">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="b1480-138">**Database name**</span></span>  
 <span data-ttu-id="b1480-139">데이터베이스 목록에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-139">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="b1480-140">**고급**</span><span class="sxs-lookup"><span data-stu-id="b1480-140">**Advanced**</span></span>  
 <span data-ttu-id="b1480-141">**고급 속성 설정** 대화 상자를 사용하여 추가 연결 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-141">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="b1480-142">자세한 내용은 [고급 속성 설정&#40;SSAS&#41;](set-advanced-properties-ssas.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1480-142">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="b1480-143">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="b1480-143">**Test Connection**</span></span>  
 <span data-ttu-id="b1480-144">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-144">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="b1480-145">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1480-145">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
