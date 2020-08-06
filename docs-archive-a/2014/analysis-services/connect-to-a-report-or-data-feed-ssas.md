---
title: 보고서 또는 데이터 피드에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connreportdatafeed.f1
ms.assetid: e0ccfb0b-e646-4de8-b7da-f88c986c96e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76dd51c32d13e64b0368267ba7ac66aa6d76a784
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648009"
---
# <a name="connect-to-a-report-or-data-feed-ssas"></a><span data-ttu-id="4c57e-102">보고서 또는 데이터 피드에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="4c57e-102">Connect to a Report or Data Feed (SSAS)</span></span>
  <span data-ttu-id="4c57e-103">**테이블 가져오기 마법사** 의 이 페이지에서는 데이터 피드에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-103">This page of the **Table Import Wizard** enables you to connect to a data feed.</span></span> <span data-ttu-id="4c57e-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="from-a-report"></a><span data-ttu-id="4c57e-105">보고서에서</span><span class="sxs-lookup"><span data-stu-id="4c57e-105">From a Report</span></span>  
 <span data-ttu-id="4c57e-106">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="4c57e-106">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="4c57e-107">데이터 피드 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-107">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="4c57e-108">**보고서 경로**</span><span class="sxs-lookup"><span data-stu-id="4c57e-108">**Report Path**</span></span>  
 <span data-ttu-id="4c57e-109">데이터 피드를 생성하는 SQL Server Reporting Services 보고서의 URL을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-109">Lists the URL for a SQL Server Reporting Services report that generates data feeds.</span></span> <span data-ttu-id="4c57e-110">**찾아보기** 를 클릭하여 보고서의 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-110">Click **Browse** to specify the URL for the report.</span></span>  
  
 <span data-ttu-id="4c57e-111">**보고서 보기**를 클릭하여 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-111">Click **View Report** to display the report.</span></span>  
  
 <span data-ttu-id="4c57e-112">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="4c57e-112">**Browse**</span></span>  
 <span data-ttu-id="4c57e-113">보고서를 사용할 수 있는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-113">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="4c57e-114">**고급**</span><span class="sxs-lookup"><span data-stu-id="4c57e-114">**Advanced**</span></span>  
 <span data-ttu-id="4c57e-115">**고급 속성 설정** 대화 상자를 사용 하 여 추가 연결 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-115">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="4c57e-116">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="4c57e-116">**Test Connection**</span></span>  
 <span data-ttu-id="4c57e-117">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-117">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="4c57e-118">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-an-azure-datamarket-dataset"></a><span data-ttu-id="4c57e-119">Azure DataMarket 데이터 세트에서</span><span class="sxs-lookup"><span data-stu-id="4c57e-119">From an Azure DataMarket Dataset</span></span>  
 <span data-ttu-id="4c57e-120">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="4c57e-120">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="4c57e-121">데이터 피드 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-121">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="4c57e-122">**데이터 피드 URL**</span><span class="sxs-lookup"><span data-stu-id="4c57e-122">**Data Feed URL**</span></span>  
 <span data-ttu-id="4c57e-123">Atom 서비스 문서(.atomsvc, .atom)의 전체 경로 또는 단일 데이터 피드의 URL을 입력하거나, **찾아보기** 를 클릭하여 Atom 서비스 문서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-123">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="4c57e-124">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="4c57e-124">**Browse**</span></span>  
 <span data-ttu-id="4c57e-125">보고서를 사용할 수 있는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-125">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="4c57e-126">사용 가능한 데이터 세트를 표시하려면 **사용 가능한 Azure DataMarket 데이터 세트 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-126">Click **View available Azure DataMarket datasets** to display available datasets.</span></span>  
  
 <span data-ttu-id="4c57e-127">**계정 키**</span><span class="sxs-lookup"><span data-stu-id="4c57e-127">**Account key**</span></span>  
 <span data-ttu-id="4c57e-128">Azure Marketplace 데이터 집합 구독에 액세스 하는 데 사용 되는 계정 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-128">Specify the account key used to access your Azure Marketplace dataset subscriptions.</span></span>  
  
 <span data-ttu-id="4c57e-129">**찾아낼**</span><span class="sxs-lookup"><span data-stu-id="4c57e-129">**Find**</span></span>  
 <span data-ttu-id="4c57e-130">Windows Live 계정과 연결된 계정 키를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-130">Locate an account key associated with a Windows Live account.</span></span>  
  
 <span data-ttu-id="4c57e-131">**내 계정 키 저장**</span><span class="sxs-lookup"><span data-stu-id="4c57e-131">**Save my account key**</span></span>  
 <span data-ttu-id="4c57e-132">데이터 연결을 사용하여 계정 키(암호화됨)를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-132">Saves the account key (encrypted) with the data connection.</span></span>  
  
 <span data-ttu-id="4c57e-133">**고급**</span><span class="sxs-lookup"><span data-stu-id="4c57e-133">**Advanced**</span></span>  
 <span data-ttu-id="4c57e-134">**고급 속성 설정** 대화 상자를 사용 하 여 추가 연결 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-134">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="4c57e-135">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="4c57e-135">**Test Connection**</span></span>  
 <span data-ttu-id="4c57e-136">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-136">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="4c57e-137">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-137">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-other-feeds"></a><span data-ttu-id="4c57e-138">다른 피드에서</span><span class="sxs-lookup"><span data-stu-id="4c57e-138">From Other Feeds</span></span>  
 <span data-ttu-id="4c57e-139">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="4c57e-139">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="4c57e-140">데이터 피드 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-140">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="4c57e-141">**데이터 피드 URL**</span><span class="sxs-lookup"><span data-stu-id="4c57e-141">**Data Feed URL**</span></span>  
 <span data-ttu-id="4c57e-142">Atom 서비스 문서(.atomsvc, .atom)의 전체 경로 또는 단일 데이터 피드의 URL을 입력하거나, **찾아보기** 를 클릭하여 Atom 서비스 문서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-142">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="4c57e-143">**모든 피드 열 포함** 을 클릭하여 모든 데이터 피드 열을 가져올지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-143">Click **Include all feed columns** to specify whether all the data feed columns are imported.</span></span>  
  
 <span data-ttu-id="4c57e-144">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="4c57e-144">**Browse**</span></span>  
 <span data-ttu-id="4c57e-145">데이터 피드를 사용할 수 있는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-145">Navigate to a location where a data feed is available.</span></span>  
  
 <span data-ttu-id="4c57e-146">**고급**</span><span class="sxs-lookup"><span data-stu-id="4c57e-146">**Advanced**</span></span>  
 <span data-ttu-id="4c57e-147">**고급 속성 설정** 대화 상자를 사용하여 추가 연결 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-147">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="4c57e-148">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="4c57e-148">**Test Connection**</span></span>  
 <span data-ttu-id="4c57e-149">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-149">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="4c57e-150">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c57e-150">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
