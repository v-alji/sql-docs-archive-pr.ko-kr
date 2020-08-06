---
title: Microsoft SQL Server 병렬 데이터 웨어하우스에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlparadatawh.f1
ms.assetid: 98c879ee-7257-40c9-bc85-6766bd3b4885
author: minewiskan
ms.author: owend
ms.openlocfilehash: 082d6b34077d1bde11b527d3bfff907073eed16e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648011"
---
# <a name="connect-to-a-microsoft-sql-server-parallel-data-warehouse-ssas"></a><span data-ttu-id="24c50-102">Microsoft SQL Server 병렬 데이터 웨어하우스에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="24c50-102">Connect to a Microsoft SQL Server Parallel Data Warehouse (SSAS)</span></span>
  <span data-ttu-id="24c50-103">**테이블 가져오기 마법사** 의 이 페이지에서는 Microsoft SQL Server PDW(병렬 데이터 웨어하우스)에 연결하기 위한 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server Parallel Data Warehouse (PDW).</span></span> <span data-ttu-id="24c50-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="24c50-105">SQL Server PDW는 방대한 병렬 처리를 통해 비용 효율적인 성능을 제공하며 확장성이 뛰어난 데이터 웨어하우스 어플라이언스입니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-105">SQL Server PDW is a highly scalable appliance that delivers performance at low cost through massively parallel processing.</span></span> <span data-ttu-id="24c50-106">SQL Server PDW에 대한 자세한 내용은 [SQL Server 2008 R2 병렬 데이터 웨어하우스(SQL Server 2008 R2 Parallel Data Warehouse)](https://go.microsoft.com/fwlink/?LinkId=150895)웹 사이트를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="24c50-106">For more information about SQL Server PDW, see the web site [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).</span></span> <span data-ttu-id="24c50-107">SQL Server 인증을 사용하여 데이터 웨어하우스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-107">You connect to the data warehouse by using SQL Server Authentication.</span></span> <span data-ttu-id="24c50-108">데이터 원본에 연결하려면 컴퓨터에 적절한 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-108">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24c50-109">이 페이지에서 데이터베이스를 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-109">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="24c50-110">하지만 가장 정보 페이지에 지정된 사용자에게 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-110">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="24c50-111">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="24c50-111">UI element list</span></span>  
 <span data-ttu-id="24c50-112">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="24c50-112">**Friendly connection name**</span></span>  
 <span data-ttu-id="24c50-113">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-113">Type a unique name for this data source connection.</span></span> <span data-ttu-id="24c50-114">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-114">This is a required field.</span></span>  
  
 <span data-ttu-id="24c50-115">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="24c50-115">**Server name**</span></span>  
 <span data-ttu-id="24c50-116">연결할 서버의 이름이나 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-116">Type the name, or IP address, of the server to connect to.</span></span>  
  
 <span data-ttu-id="24c50-117">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="24c50-117">**User name**</span></span>  
 <span data-ttu-id="24c50-118">데이터베이스 연결의 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="24c50-119">이 사용자 이름은 데이터 원본에 대한 연결 문자열을 구성할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-119">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="24c50-120">이러한 자격 증명은 테이블 속성 창과 가져오기 마법사에서 데이터를 미리 보거나 필터링할 때도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-120">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="24c50-121">이러한 자격 증명은 데이터를 가져오거나 새로 고칠 때는 사용되지 않습니다. 이 경우에는 가장 정보 페이지에서 지정한 Windows 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-121">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="24c50-122">**암호**</span><span class="sxs-lookup"><span data-stu-id="24c50-122">**Password**</span></span>  
 <span data-ttu-id="24c50-123">데이터베이스 연결의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-123">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="24c50-124">**내 암호 저장**</span><span class="sxs-lookup"><span data-stu-id="24c50-124">**Save my password**</span></span>  
 <span data-ttu-id="24c50-125">**암호** 상자에 입력한 암호를 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-125">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="24c50-126">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="24c50-126">**Database name**</span></span>  
 <span data-ttu-id="24c50-127">데이터베이스 목록에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-127">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="24c50-128">**고급**</span><span class="sxs-lookup"><span data-stu-id="24c50-128">**Advanced**</span></span>  
 <span data-ttu-id="24c50-129">**고급 속성 설정** 대화 상자를 사용하여 추가 연결 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-129">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="24c50-130">자세한 내용은 [고급 속성 설정&#40;SSAS&#41;](set-advanced-properties-ssas.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24c50-130">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="24c50-131">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="24c50-131">**Test Connection**</span></span>  
 <span data-ttu-id="24c50-132">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-132">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="24c50-133">연결의 성공 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="24c50-133">A message displays and indicates whether the connection is successful.</span></span>  
  
  
