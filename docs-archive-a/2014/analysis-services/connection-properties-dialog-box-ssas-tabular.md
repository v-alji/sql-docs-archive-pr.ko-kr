---
title: 연결 속성 대화 상자 (SSAS-테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.ConnectionProperties.F1
ms.assetid: 17bae8ae-2ba0-4978-be70-61c687f59d54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e4b0360d59f43bc932f68a846f239c4873a5aa9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647993"
---
# <a name="connection-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="83c3f-102">연결 속성 대화 상자(SSAS - 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="83c3f-102">Connection Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="83c3f-103">이 페이지를 사용하여 SQL Server Management Studio에서 테이블 형식 모델 데이터베이스에 사용되는 데이터 원본의 연결 속성을 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-103">Use this page to view or modify in SQL Server Management Studio the connection properties of a data source used by a tabular model database.</span></span>  
  
 <span data-ttu-id="83c3f-104">이 대화 상자에서는 타임스탬프, 기타 설명 정보 및 연결 특성을 결정하는 사용자 지정 가능 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-104">This dialog box provides timestamps and other descriptive information, plus customizable properties that determine characteristics of the connection.</span></span>  
  
## <a name="options"></a><span data-ttu-id="83c3f-105">옵션</span><span class="sxs-lookup"><span data-stu-id="83c3f-105">Options</span></span>  
  
|<span data-ttu-id="83c3f-106">용어</span><span class="sxs-lookup"><span data-stu-id="83c3f-106">Term</span></span>|<span data-ttu-id="83c3f-107">정의</span><span class="sxs-lookup"><span data-stu-id="83c3f-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="83c3f-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="83c3f-108">**Name**</span></span>|<span data-ttu-id="83c3f-109">데이터 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-109">Specifies the name of the data source.</span></span>|  
|<span data-ttu-id="83c3f-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="83c3f-110">**ID**</span></span>|<span data-ttu-id="83c3f-111">데이터 원본 개체의 식별자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-111">Displays the identifier of the data source object.</span></span>|  
|<span data-ttu-id="83c3f-112">**설명**</span><span class="sxs-lookup"><span data-stu-id="83c3f-112">**Description**</span></span>|<span data-ttu-id="83c3f-113">데이터 원본 개체의 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-113">Displays the description of the data source object.</span></span>|  
|<span data-ttu-id="83c3f-114">**생성된 타임스탬프**</span><span class="sxs-lookup"><span data-stu-id="83c3f-114">**Create Timestamp**</span></span>|<span data-ttu-id="83c3f-115">데이터베이스를 만든 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-115">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="83c3f-116">**최종 스키마 업데이트**</span><span class="sxs-lookup"><span data-stu-id="83c3f-116">**Last Schema Update**</span></span>|<span data-ttu-id="83c3f-117">데이터베이스에 대한 메타데이터를 마지막으로 업데이트한 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-117">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="83c3f-118">**연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="83c3f-118">**Connection String**</span></span>|<span data-ttu-id="83c3f-119">모델에 데이터를 제공하는 데이터 원본에 연결하는 데 사용되는 연결 문자열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-119">Displays the connection string used to connect to the data source that provides data to the model.</span></span>|  
|<span data-ttu-id="83c3f-120">**최대 연결 수**</span><span class="sxs-lookup"><span data-stu-id="83c3f-120">**Maximum Number of Connections**</span></span>|<span data-ttu-id="83c3f-121">이 데이터베이스에 대한 최대 클라이언트 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-121">Specifies the maximum number of client connections to this database.</span></span>|  
|<span data-ttu-id="83c3f-122">**격리**</span><span class="sxs-lookup"><span data-stu-id="83c3f-122">**Isolation**</span></span>|<span data-ttu-id="83c3f-123">유효한 값은 ReadCommitted 또는 Snapshot입니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-123">Valid values are ReadCommitted or Snapshot.</span></span> <span data-ttu-id="83c3f-124">자세한 내용은 [Isolation 요소&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83c3f-124">For more information, see [Isolation Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl).</span></span>|  
|<span data-ttu-id="83c3f-125">**쿼리 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="83c3f-125">**Query Timeout**</span></span>|<span data-ttu-id="83c3f-126">데이터 검색 시도의 제한 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-126">Specifies the time, in seconds, after which an attempt to retrieve data is timed out.</span></span>|  
|<span data-ttu-id="83c3f-127">**관리 공급자**</span><span class="sxs-lookup"><span data-stu-id="83c3f-127">**Managed Provider**</span></span>|<span data-ttu-id="83c3f-128">관리 공급자의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-128">Specifies the name of the managed provider.</span></span> <span data-ttu-id="83c3f-129">데이터 원본 연결에서 네이티브 OLE DB 공급자를 사용하는 경우에는 이 값이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-129">If the data source connection uses a native OLE DB provider, this value is empty.</span></span>|  
|<span data-ttu-id="83c3f-130">**가장 정보**</span><span class="sxs-lookup"><span data-stu-id="83c3f-130">**Impersonation Info**</span></span>|<span data-ttu-id="83c3f-131">데이터, 관계형 데이터 저장소에 대해 DirectQuery를 통해 실행된 쿼리, 아웃오브 라인 바인딩, 원격 파티션, 대상에서 원본으로의 데이터베이스 동기화를 처리하거나 새로 고칠 때 데이터베이스 연결에 사용되는 가장 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-131">Specifies the impersonation account used for database connections when processing or refreshing data, queries that run against a relational data store (via DirectQuery), out-of-line bindings, remote partitions, and database synchronization from target to source.</span></span><br /><br /> <span data-ttu-id="83c3f-132">유효한 값은 Analysis Services 서비스 계정 또는 특정 Windows 자격 증명 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-132">Valid values include the Analysis Services service account or a specific set of Windows credentials.</span></span> <span data-ttu-id="83c3f-133">**현재 사용자의 자격 증명 사용** 이나 **상속**을 지정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="83c3f-133">Do not specify **Use the credentials of the current user** or **Inherit**.</span></span> <span data-ttu-id="83c3f-134">이러한 자격 증명 옵션은 테이블 형식 모델 데이터베이스에는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83c3f-134">Those credential options are not supported for a tabular model database.</span></span>|  
  
  
