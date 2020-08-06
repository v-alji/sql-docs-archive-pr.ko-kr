---
title: MSSQLSERVER_33085 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d774ab115c2d0ddbbd7b35c7e32db17e39fcb2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650055"
---
# <a name="mssqlserver_33085"></a><span data-ttu-id="9e686-102">MSSQLSERVER_33085</span><span class="sxs-lookup"><span data-stu-id="9e686-102">MSSQLSERVER_33085</span></span>
    
## <a name="details"></a><span data-ttu-id="9e686-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9e686-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e686-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9e686-104">Product Name</span></span>|<span data-ttu-id="9e686-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9e686-105">SQL Server</span></span>|  
|<span data-ttu-id="9e686-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9e686-106">Event ID</span></span>|<span data-ttu-id="9e686-107">33085</span><span class="sxs-lookup"><span data-stu-id="9e686-107">33085</span></span>|  
|<span data-ttu-id="9e686-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9e686-108">Event Source</span></span>|<span data-ttu-id="9e686-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9e686-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9e686-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9e686-110">Component</span></span>|<span data-ttu-id="9e686-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9e686-111">SQLEngine</span></span>|  
|<span data-ttu-id="9e686-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9e686-112">Symbolic Name</span></span>|<span data-ttu-id="9e686-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="9e686-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span></span>|  
|<span data-ttu-id="9e686-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9e686-114">Message Text</span></span>|<span data-ttu-id="9e686-115">암호화 공급자 라이브러리 '%.\*ls'에서 하나 이상의 메서드를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e686-115">One or more methods cannot be found in cryptographic provider library '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9e686-116">설명</span><span class="sxs-lookup"><span data-stu-id="9e686-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9e686-117">에서 위의 오류 메시지에 나열된 암호화 공급자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e686-117">was unable to use the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="9e686-118">암호화 공급자가 필요한 메서드를 지원하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9e686-118">The cryptographic provider did not support a required method.</span></span> <span data-ttu-id="9e686-119">오류의 상태는 찾지 못한 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e686-119">The state of the error indicates which method was not found.</span></span>  
  
|<span data-ttu-id="9e686-120">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="9e686-120">State</span></span>|<span data-ttu-id="9e686-121">Description</span><span class="sxs-lookup"><span data-stu-id="9e686-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9e686-122">1</span><span class="sxs-lookup"><span data-stu-id="9e686-122">1</span></span>|<span data-ttu-id="9e686-123">SqlCryptInitializeProvider</span><span class="sxs-lookup"><span data-stu-id="9e686-123">SqlCryptInitializeProvider</span></span>|  
|<span data-ttu-id="9e686-124">2</span><span class="sxs-lookup"><span data-stu-id="9e686-124">2</span></span>|<span data-ttu-id="9e686-125">SqlCryptFreeProvider</span><span class="sxs-lookup"><span data-stu-id="9e686-125">SqlCryptFreeProvider</span></span>|  
|<span data-ttu-id="9e686-126">3</span><span class="sxs-lookup"><span data-stu-id="9e686-126">3</span></span>|<span data-ttu-id="9e686-127">SqlCryptOpenSession</span><span class="sxs-lookup"><span data-stu-id="9e686-127">SqlCryptOpenSession</span></span>|  
|<span data-ttu-id="9e686-128">4</span><span class="sxs-lookup"><span data-stu-id="9e686-128">4</span></span>|<span data-ttu-id="9e686-129">SqlCryptCloseSession</span><span class="sxs-lookup"><span data-stu-id="9e686-129">SqlCryptCloseSession</span></span>|  
|<span data-ttu-id="9e686-130">5</span><span class="sxs-lookup"><span data-stu-id="9e686-130">5</span></span>|<span data-ttu-id="9e686-131">SqlCryptGetProviderInfo</span><span class="sxs-lookup"><span data-stu-id="9e686-131">SqlCryptGetProviderInfo</span></span>|  
|<span data-ttu-id="9e686-132">6</span><span class="sxs-lookup"><span data-stu-id="9e686-132">6</span></span>|<span data-ttu-id="9e686-133">SqlCryptGetNextAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="9e686-133">SqlCryptGetNextAlgorithmId</span></span>|  
|<span data-ttu-id="9e686-134">7</span><span class="sxs-lookup"><span data-stu-id="9e686-134">7</span></span>|<span data-ttu-id="9e686-135">SqlCryptGetAlgorithmInfo</span><span class="sxs-lookup"><span data-stu-id="9e686-135">SqlCryptGetAlgorithmInfo</span></span>|  
|<span data-ttu-id="9e686-136">8</span><span class="sxs-lookup"><span data-stu-id="9e686-136">8</span></span>|<span data-ttu-id="9e686-137">SqlCryptCreateKey</span><span class="sxs-lookup"><span data-stu-id="9e686-137">SqlCryptCreateKey</span></span>|  
|<span data-ttu-id="9e686-138">9</span><span class="sxs-lookup"><span data-stu-id="9e686-138">9</span></span>|<span data-ttu-id="9e686-139">SqlCryptDropKey</span><span class="sxs-lookup"><span data-stu-id="9e686-139">SqlCryptDropKey</span></span>|  
|<span data-ttu-id="9e686-140">10</span><span class="sxs-lookup"><span data-stu-id="9e686-140">10</span></span>|<span data-ttu-id="9e686-141">SqlCryptGetNextKeyId</span><span class="sxs-lookup"><span data-stu-id="9e686-141">SqlCryptGetNextKeyId</span></span>|  
|<span data-ttu-id="9e686-142">11</span><span class="sxs-lookup"><span data-stu-id="9e686-142">11</span></span>|<span data-ttu-id="9e686-143">SqlCryptGetKeyInfoByKeyId</span><span class="sxs-lookup"><span data-stu-id="9e686-143">SqlCryptGetKeyInfoByKeyId</span></span>|  
|<span data-ttu-id="9e686-144">12</span><span class="sxs-lookup"><span data-stu-id="9e686-144">12</span></span>|<span data-ttu-id="9e686-145">SqlCryptGetKeyInfoByThumb</span><span class="sxs-lookup"><span data-stu-id="9e686-145">SqlCryptGetKeyInfoByThumb</span></span>|  
|<span data-ttu-id="9e686-146">13</span><span class="sxs-lookup"><span data-stu-id="9e686-146">13</span></span>|<span data-ttu-id="9e686-147">SqlCryptGetKeyInfoByName</span><span class="sxs-lookup"><span data-stu-id="9e686-147">SqlCryptGetKeyInfoByName</span></span>|  
|<span data-ttu-id="9e686-148">14</span><span class="sxs-lookup"><span data-stu-id="9e686-148">14</span></span>|<span data-ttu-id="9e686-149">SqlCryptExportKey</span><span class="sxs-lookup"><span data-stu-id="9e686-149">SqlCryptExportKey</span></span>|  
|<span data-ttu-id="9e686-150">15</span><span class="sxs-lookup"><span data-stu-id="9e686-150">15</span></span>|<span data-ttu-id="9e686-151">SqlCryptImportKey</span><span class="sxs-lookup"><span data-stu-id="9e686-151">SqlCryptImportKey</span></span>|  
|<span data-ttu-id="9e686-152">16</span><span class="sxs-lookup"><span data-stu-id="9e686-152">16</span></span>|<span data-ttu-id="9e686-153">SqlCryptEncrypt</span><span class="sxs-lookup"><span data-stu-id="9e686-153">SqlCryptEncrypt</span></span>|  
|<span data-ttu-id="9e686-154">17</span><span class="sxs-lookup"><span data-stu-id="9e686-154">17</span></span>|<span data-ttu-id="9e686-155">SqlCryptDecrypt</span><span class="sxs-lookup"><span data-stu-id="9e686-155">SqlCryptDecrypt</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="9e686-156">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9e686-156">User Action</span></span>  
 <span data-ttu-id="9e686-157">암호화 공급자에게 자세한 정보를 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="9e686-157">Contact the cryptographic provider for more information.</span></span>  
  
  
