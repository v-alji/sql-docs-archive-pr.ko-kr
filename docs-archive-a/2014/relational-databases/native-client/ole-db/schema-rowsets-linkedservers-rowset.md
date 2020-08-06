---
title: LINKEDSERVERS 행 집합(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
author: rothja
ms.author: jroth
ms.openlocfilehash: 80eded31ebae744e272757a53a7fd1f4b56bf358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647647"
---
# <a name="linkedservers-rowset-ole-db"></a><span data-ttu-id="b3b4b-102">LINKEDSERVERS 행 집합(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="b3b4b-102">LINKEDSERVERS Rowset (OLE DB)</span></span>
  <span data-ttu-id="b3b4b-103">**LINKEDSERVERS** 행 집합은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 분산 쿼리에 참여할 수 있는 조직 데이터 원본을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-103">The **LINKEDSERVERS** rowset enumerates organization data sources that can participate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries.</span></span>  
  
 <span data-ttu-id="b3b4b-104">**LINKEDSERVERS** 행 집합에는 다음 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-104">The **LINKEDSERVERS** rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="b3b4b-105">열 이름</span><span class="sxs-lookup"><span data-stu-id="b3b4b-105">Column name</span></span>|<span data-ttu-id="b3b4b-106">유형 표시기</span><span class="sxs-lookup"><span data-stu-id="b3b4b-106">Type indicator</span></span>|<span data-ttu-id="b3b4b-107">Description</span><span class="sxs-lookup"><span data-stu-id="b3b4b-107">Description</span></span>|  
|-----------------|--------------------|-----------------|  
|<span data-ttu-id="b3b4b-108">SVR_NAME</span><span class="sxs-lookup"><span data-stu-id="b3b4b-108">SVR_NAME</span></span>|<span data-ttu-id="b3b4b-109">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="b3b4b-109">DBTYPE_WSTR</span></span>|<span data-ttu-id="b3b4b-110">연결된 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-110">Name of a linked server.</span></span>|  
|<span data-ttu-id="b3b4b-111">SVR_PRODUCT</span><span class="sxs-lookup"><span data-stu-id="b3b4b-111">SVR_PRODUCT</span></span>|<span data-ttu-id="b3b4b-112">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="b3b4b-112">DBTYPE_WSTR</span></span>|<span data-ttu-id="b3b4b-113">연결된 서버 이름이 나타내는 데이터 저장소 유형을 식별하는 제조업체 또는 기타 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-113">Manufacturer or other name identifying the type of data store represented by the name of the linked server.</span></span>|  
|<span data-ttu-id="b3b4b-114">SVR_PROVIDERNAME</span><span class="sxs-lookup"><span data-stu-id="b3b4b-114">SVR_PROVIDERNAME</span></span>|<span data-ttu-id="b3b4b-115">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="b3b4b-115">DBTYPE_WSTR</span></span>|<span data-ttu-id="b3b4b-116">서버 데이터를 이용할 때 사용되는 OLE DB 공급자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-116">Friendly name of the OLE DB provider used to consume data from the server.</span></span>|  
|<span data-ttu-id="b3b4b-117">SVR_DATASOURCE</span><span class="sxs-lookup"><span data-stu-id="b3b4b-117">SVR_DATASOURCE</span></span>|<span data-ttu-id="b3b4b-118">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="b3b4b-118">DBTYPE_WSTR</span></span>|<span data-ttu-id="b3b4b-119">공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_DATASOURCE 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-119">OLE DB DBPROP_INIT_DATASOURCE string used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="b3b4b-120">SVR_PROVIDERSTRING</span><span class="sxs-lookup"><span data-stu-id="b3b4b-120">SVR_PROVIDERSTRING</span></span>|<span data-ttu-id="b3b4b-121">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="b3b4b-121">DBTYPE_WSTR</span></span>|<span data-ttu-id="b3b4b-122">공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_PROVIDERSTRING 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-122">OLE DB DBPROP_INIT_PROVIDERSTRING value used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="b3b4b-123">SVR_LOCATION</span><span class="sxs-lookup"><span data-stu-id="b3b4b-123">SVR_LOCATION</span></span>|<span data-ttu-id="b3b4b-124">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="b3b4b-124">DBTYPE_WSTR</span></span>|<span data-ttu-id="b3b4b-125">공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_LOCATION 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-125">OLE DB DBPROP_INIT_LOCATION string used to acquire a data source from the provider.</span></span>|  
  
 <span data-ttu-id="b3b4b-126">행 집합은 SRV_NAME을 기준으로 정렬되며 SRV_NAME에서 하나의 제한이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3b4b-126">The rowset is sorted on SRV_NAME and a single restriction is supported on SRV_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b4b-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3b4b-127">See Also</span></span>  
 [<span data-ttu-id="b3b4b-128">스키마 행 집합 지원&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b3b4b-128">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
  
