---
title: 데이터 수집기의 속성 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05172c2c831ec649269512a625be069cdc67047a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734143"
---
# <a name="configure-properties-of-a-data-collector"></a><span data-ttu-id="d5139-102">데이터 수집기의 속성 구성</span><span class="sxs-lookup"><span data-stu-id="d5139-102">Configure Properties of a Data Collector</span></span>
  <span data-ttu-id="d5139-103">이 항목에서는 데이터 수집기의 속성을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-103">This topic discusses how you can configure the properties of a data collector.</span></span>  
  
## <a name="data-collection-properties-general-tab"></a><span data-ttu-id="d5139-104">데이터 컬렉션 속성(일반 탭)</span><span class="sxs-lookup"><span data-stu-id="d5139-104">Data Collection Properties (General Tab)</span></span>  
 <span data-ttu-id="d5139-105">이 페이지를 사용하여 관리 데이터 웨어하우스에 대한 설정을 구성하고 수집한 데이터를 데이터 웨어하우스에 업로드하기 전에 저장하는 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-105">Use this page to configure settings for the management data warehouse and specify where collected data should be stored before it is uploaded to the data warehouse.</span></span>  
  
 <span data-ttu-id="d5139-106">**데이터 컬렉션 활성화**</span><span class="sxs-lookup"><span data-stu-id="d5139-106">**Enable Data Collection**</span></span>  
 <span data-ttu-id="d5139-107">데이터 컬렉션을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-107">Select to enable data collection.</span></span> <span data-ttu-id="d5139-108">이렇게 하면 sp_syscollector_enable_collector 저장 프로시저를 실행하는 것과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-108">This has the same effect as running the sp_syscollector_enable_collector stored procedure.</span></span> <span data-ttu-id="d5139-109">이 확인란의 선택을 취소하면 데이터 컬렉션이 사용되지 않고 sp_syscollector_disable_collector 저장 프로시저를 실행하는 것과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-109">Clearing this check box disables data collection and has the same effect as running the sp_syscollector_disable_collector stored procedure.</span></span>  
  
 <span data-ttu-id="d5139-110">**Server**</span><span class="sxs-lookup"><span data-stu-id="d5139-110">**Server**</span></span>  
 <span data-ttu-id="d5139-111">관리 데이터 웨어하우스를 호스팅할 서버의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-111">Displays the name of the server that will host the management data warehouse</span></span>  
  
 <span data-ttu-id="d5139-112">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="d5139-112">**Database name**</span></span>  
 <span data-ttu-id="d5139-113">관리 데이터 웨어하우스에 사용되는 관계형 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-113">Displays the name of the relational database that is used for the management data warehouse.</span></span>  
  
 <span data-ttu-id="d5139-114">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="d5139-114">**Test Connection**</span></span>  
 <span data-ttu-id="d5139-115">데이터 컬렉션이 구성될 때 제공된 정보를 사용하여 지정된 **서버** 에 대한 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-115">Test the connection to the specified **Server** using information provided when data collection is configured.</span></span>  
  
 <span data-ttu-id="d5139-116">**캐시 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="d5139-116">**Cache directory**</span></span>  
 <span data-ttu-id="d5139-117">수집된 데이터를 관리 데이터 웨어하우스에 업로드하기 전에 데이터를 수집하는 시스템에 저장할 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-117">Specifies the directory where collected data is stored on the system collecting the data before it is uploaded to the management data warehouse.</span></span> <span data-ttu-id="d5139-118">**캐시 디렉터리** 를 지정하지 않으면 데이터 수집기가 %TEMP% 및 %TMP% 환경 변수를 찾고 이러한 위치 중 하나를 임시 스토리지의 기본 위치로 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-118">If **Cache directory** is not specified, the data collector attempts to locate the %TEMP% and %TMP% environment variables and use one these locations as the default location for temporary storage.</span></span> <span data-ttu-id="d5139-119">이러한 환경 변수가 구성되어 있지 않으면 오류가 발생하고 캐시 디렉터리를 만들라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-119">If these environment variables are not configured, an error occurs and you are prompted to create a cache directory.</span></span>  
  
## <a name="data-collection-properties-advanced-tab"></a><span data-ttu-id="d5139-120">데이터 컬렉션 속성(고급 탭)</span><span class="sxs-lookup"><span data-stu-id="d5139-120">Data Collection Properties (Advanced Tab)</span></span>  
 <span data-ttu-id="d5139-121">이 페이지를 사용하여 관리 데이터 웨어하우스에 연결하는 데 사용되는 다시 시도 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-121">Use this page to configure the retry settings for the connection to the management data warehouse.</span></span>  
  
 <span data-ttu-id="d5139-122">**업로드 실패 시의 다시 시도 횟수**</span><span class="sxs-lookup"><span data-stu-id="d5139-122">**Number of times to retry if upload fails**</span></span>  
 <span data-ttu-id="d5139-123">관리 데이터 웨어하우스에 대한 업로드가 실패할 경우 다시 시도할 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-123">Specifies the number of times to retry an upload to the management data warehouse if an upload fails.</span></span> <span data-ttu-id="d5139-124">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="d5139-124">The default is 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5139-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5139-125">See Also</span></span>  
 <span data-ttu-id="d5139-126">[데이터 컬렉션 관리](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="d5139-126">[Manage Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="d5139-127">관리 데이터 웨어하우스 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d5139-127">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
