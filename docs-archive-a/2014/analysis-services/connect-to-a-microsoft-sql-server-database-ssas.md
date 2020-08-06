---
title: Microsoft SQL Server 데이터베이스에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserverdb.f1
ms.assetid: 6ebfe029-dbba-4f0d-a556-328e79ef629f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64267cd65836cf8e6c8d8b26a177de595894b601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648018"
---
# <a name="connect-to-a-microsoft-sql-server-database-ssas"></a><span data-ttu-id="9a53f-102">Microsoft SQL Server 데이터베이스에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="9a53f-102">Connect to a Microsoft SQL Server Database (SSAS)</span></span>
  <span data-ttu-id="9a53f-103">**테이블 가져오기 마법사** 의 이 페이지에서는 Microsoft SQL Server 데이터베이스에 연결하기 위한 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server database.</span></span> <span data-ttu-id="9a53f-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="9a53f-105">데이터 원본에 연결하려면 컴퓨터에 적절한 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a53f-106">이 페이지에서 데이터베이스를 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="9a53f-107">하지만 가장 정보 페이지에 지정된 사용자에게 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9a53f-108">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="9a53f-108">UI element list</span></span>  
 <span data-ttu-id="9a53f-109">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="9a53f-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="9a53f-110">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="9a53f-111">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-111">This is a required field.</span></span>  
  
 <span data-ttu-id="9a53f-112">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="9a53f-112">**Server name**</span></span>  
 <span data-ttu-id="9a53f-113">연결할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 이름을 선택하거나, 해당 이름 또는 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-113">Select the name, or type the name or IP address, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to.</span></span>  
  
 <span data-ttu-id="9a53f-114">마침표(.), (local) 또는 localhost를 사용하여 로컬 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-114">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
 <span data-ttu-id="9a53f-115">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="9a53f-115">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="9a53f-116">Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 인스턴스에 연결할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-116">Specify whether Windows Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9a53f-117">Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 사용하여 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-117">Windows Authentication mode enables a user to connect by using a Windows user account.</span></span> <span data-ttu-id="9a53f-118">가능하면 Windows 인증을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="9a53f-118">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="9a53f-119">Windows 인증을 사용하는 경우 현재 사용자의 자격 증명을 사용하여 테이블 속성 창 및 가져오기 마법사에서 데이터를 미리 보거나 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-119">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="9a53f-120">이러한 자격 증명은 데이터를 가져오거나 새로 고칠 때는 사용되지 않습니다. 이 경우에는 가장 정보 페이지에서 지정한 Windows 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-120">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation information page are used instead.</span></span>  
  
 <span data-ttu-id="9a53f-121">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="9a53f-121">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="9a53f-122">SQL Server 인증을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 인스턴스에 연결할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-122">Specify whether SQL Server Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9a53f-123">SQL Server 인증을 사용하는 경우 SQL Server는 SQL Server 로그인 계정이 설정되어 있고 지정한 암호가 이전에 기록한 암호와 일치하는지를 자체적으로 확인하여 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-123">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="9a53f-124">SQL Server 인증은 데이터 원본에 대한 연결 문자열을 구성할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-124">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="9a53f-125">이러한 자격 증명은 테이블 속성 창과 가져오기 마법사에서 데이터를 미리 보거나 필터링할 때도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-125">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="9a53f-126">이러한 자격 증명은 데이터를 가져오거나 새로 고칠 때는 사용되지 않습니다. 이 경우에는 가장 정보 페이지에서 지정한 Windows 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-126">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="9a53f-127">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="9a53f-127">**User name**</span></span>  
 <span data-ttu-id="9a53f-128">데이터베이스 연결의 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-128">Specify a user name for the database connection.</span></span> <span data-ttu-id="9a53f-129">이 옵션은 SQL Server 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-129">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="9a53f-130">**암호**</span><span class="sxs-lookup"><span data-stu-id="9a53f-130">**Password**</span></span>  
 <span data-ttu-id="9a53f-131">데이터베이스 연결의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-131">Specify a password for the database connection.</span></span> <span data-ttu-id="9a53f-132">이 옵션은 SQL Server 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-132">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="9a53f-133">**내 암호 저장**</span><span class="sxs-lookup"><span data-stu-id="9a53f-133">**Save my password**</span></span>  
 <span data-ttu-id="9a53f-134">**암호** 상자에 입력한 암호를 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-134">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="9a53f-135">이 옵션은 SQL Server 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-135">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="9a53f-136">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="9a53f-136">**Database name**</span></span>  
 <span data-ttu-id="9a53f-137">데이터베이스 목록에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-137">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="9a53f-138">**고급**</span><span class="sxs-lookup"><span data-stu-id="9a53f-138">**Advanced**</span></span>  
 <span data-ttu-id="9a53f-139">**고급 속성 설정** 대화 상자를 사용하여 추가 연결 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-139">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="9a53f-140">자세한 내용은 [고급 속성 설정&#40;SSAS&#41;](set-advanced-properties-ssas.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a53f-140">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="9a53f-141">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="9a53f-141">**Test Connection**</span></span>  
 <span data-ttu-id="9a53f-142">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-142">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="9a53f-143">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a53f-143">A message is displayed indicating whether the connection was successful.</span></span>  
  
  
