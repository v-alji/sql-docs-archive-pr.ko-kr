---
title: Sybase 데이터베이스에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsybasedb.f1
ms.assetid: b4ebdc57-8b2a-4950-b489-88360e6c82c5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 111334ca21d04ad27d306fcb27a6d9b8210e26eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648010"
---
# <a name="connect-to-a-sybase-database-ssas"></a><span data-ttu-id="d6e71-102">Sybase 데이터베이스에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="d6e71-102">Connect to a Sybase Database (SSAS)</span></span>
  <span data-ttu-id="d6e71-103">**테이블 가져오기 마법사** 의 이 페이지에서는 Sybase 데이터베이스에 연결하기 위한 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-103">This page of the **Table Import Wizard** enables you to specify settings to connect to an Sybase database.</span></span> <span data-ttu-id="d6e71-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="d6e71-105">데이터 원본에 연결하려면 컴퓨터에 적절한 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6e71-106">이 페이지에서 데이터베이스를 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="d6e71-107">하지만 가장 정보 페이지에 지정된 사용자에게 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d6e71-108">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="d6e71-108">UI element list</span></span>  
 <span data-ttu-id="d6e71-109">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="d6e71-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="d6e71-110">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="d6e71-111">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-111">This is a required field.</span></span>  
  
 <span data-ttu-id="d6e71-112">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="d6e71-112">**Server name**</span></span>  
 <span data-ttu-id="d6e71-113">연결할 서버 인스턴스를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-113">Type or select the server instance to connect to.</span></span>  
  
 <span data-ttu-id="d6e71-114">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="d6e71-114">**User name**</span></span>  
 <span data-ttu-id="d6e71-115">데이터베이스 연결의 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-115">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="d6e71-116">이 사용자 이름은 데이터 원본에 대한 연결 문자열을 구성할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-116">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="d6e71-117">이러한 자격 증명은 테이블 속성 창과 가져오기 마법사에서 데이터를 미리 보거나 필터링할 때도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-117">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="d6e71-118">이러한 자격 증명은 데이터를 가져오거나 새로 고칠 때는 사용되지 않습니다. 이 경우에는 가장 정보 페이지에서 지정한 Windows 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-118">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="d6e71-119">**암호**</span><span class="sxs-lookup"><span data-stu-id="d6e71-119">**Password**</span></span>  
 <span data-ttu-id="d6e71-120">데이터베이스 연결의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="d6e71-121">**내 암호 저장**</span><span class="sxs-lookup"><span data-stu-id="d6e71-121">**Save my password**</span></span>  
 <span data-ttu-id="d6e71-122">**암호** 상자에 입력한 암호를 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="d6e71-123">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="d6e71-123">**Database Name**</span></span>  
 <span data-ttu-id="d6e71-124">데이터베이스 목록에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-124">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="d6e71-125">**고급**</span><span class="sxs-lookup"><span data-stu-id="d6e71-125">**Advanced**</span></span>  
 <span data-ttu-id="d6e71-126">**고급 속성 설정** 대화 상자를 사용하여 추가 연결 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-126">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="d6e71-127">자세한 내용은 [고급 속성 설정&#40;SSAS&#41;](set-advanced-properties-ssas.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6e71-127">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="d6e71-128">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="d6e71-128">**Test Connection**</span></span>  
 <span data-ttu-id="d6e71-129">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-129">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="d6e71-130">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6e71-130">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
