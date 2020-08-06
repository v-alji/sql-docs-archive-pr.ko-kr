---
title: Microsoft Access 데이터베이스에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connaccessdb.f1
ms.assetid: 9fa81839-dd8b-41d3-915e-c774a707ed53
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb180a754b6bc276d588997117eb84fd1a5a873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648019"
---
# <a name="connect-to-a-microsoft-access-database-ssas"></a><span data-ttu-id="4c1ba-102">Microsoft Access 데이터베이스에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="4c1ba-102">Connect to a Microsoft Access Database (SSAS)</span></span>
  <span data-ttu-id="4c1ba-103">**테이블 가져오기 마법사** 의 이 페이지에서는 Microsoft Access 데이터베이스에 연결하기 위한 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft Access database.</span></span> <span data-ttu-id="4c1ba-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="4c1ba-105">Microsoft Access 데이터베이스에 연결하려면 컴퓨터에 적절한 ACE 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-105">To connect to a Microsoft Access database, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="4c1ba-106">자세한 내용은 [지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;](tabular-models/data-sources-supported-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c1ba-107">이 페이지에서 파일을 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="4c1ba-108">하지만 가장 정보 페이지에 지정된 사용자에게 선택한 파일을 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4c1ba-109">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="4c1ba-109">UI element list</span></span>  
 <span data-ttu-id="4c1ba-110">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="4c1ba-111">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="4c1ba-112">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-112">This is a required field.</span></span>  
  
 <span data-ttu-id="4c1ba-113">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-113">**Database name**</span></span>  
 <span data-ttu-id="4c1ba-114">Microsoft Access 데이터베이스 파일에 대한 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-114">Specify the full path for a Microsoft Access database file.</span></span>  
  
 <span data-ttu-id="4c1ba-115">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-115">**Browse**</span></span>  
 <span data-ttu-id="4c1ba-116">Microsoft Access 데이터베이스 파일을 사용할 수 있는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-116">Navigate to a location where a Microsoft Access database file is available.</span></span>  
  
 <span data-ttu-id="4c1ba-117">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-117">**User name**</span></span>  
 <span data-ttu-id="4c1ba-118">데이터베이스 연결의 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="4c1ba-119">**암호**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-119">**Password**</span></span>  
 <span data-ttu-id="4c1ba-120">데이터베이스 연결의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="4c1ba-121">**내 암호 저장**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-121">**Save my password**</span></span>  
 <span data-ttu-id="4c1ba-122">**암호** 상자에 입력한 암호를 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="4c1ba-123">**고급**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-123">**Advanced**</span></span>  
 <span data-ttu-id="4c1ba-124">**고급 속성 설정** 대화 상자를 사용하여 추가 연결 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="4c1ba-125">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="4c1ba-125">**Test Connection**</span></span>  
 <span data-ttu-id="4c1ba-126">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-126">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="4c1ba-127">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ba-127">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
