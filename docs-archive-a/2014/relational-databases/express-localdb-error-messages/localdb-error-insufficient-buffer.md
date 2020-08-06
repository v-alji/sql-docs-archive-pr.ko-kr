---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 934683cfca1a9a9c0596071824c21a0045e6ebab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660596"
---
# <a name="localdb_error_insufficient_buffer"></a><span data-ttu-id="64766-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="64766-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>
    
## <a name="details"></a><span data-ttu-id="64766-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="64766-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64766-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="64766-104">Product Name</span></span>|<span data-ttu-id="64766-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="64766-105">SQL Server</span></span>|  
|<span data-ttu-id="64766-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="64766-106">Event ID</span></span>|<span data-ttu-id="64766-107">276</span><span class="sxs-lookup"><span data-stu-id="64766-107">276</span></span>|  
|<span data-ttu-id="64766-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="64766-108">Event Source</span></span>|<span data-ttu-id="64766-109">SQL Server 로컬 데이터베이스 런타임 12.0</span><span class="sxs-lookup"><span data-stu-id="64766-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="64766-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="64766-110">Component</span></span>|<span data-ttu-id="64766-111">로컬 데이터베이스 런타임 API</span><span class="sxs-lookup"><span data-stu-id="64766-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="64766-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="64766-112">Message Text</span></span>|<span data-ttu-id="64766-113">로컬 데이터베이스 인스턴스 API 메서드로 전달된 버퍼의 크기가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="64766-113">The buffer passed to the Local Database instance API method has insufficient size.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="64766-114">설명</span><span class="sxs-lookup"><span data-stu-id="64766-114">Explanation</span></span>  
 <span data-ttu-id="64766-115">입력 버퍼가 너무 짧은데 잘림이 요청되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="64766-115">The input buffer is too short, and truncation was not requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="64766-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="64766-116">User Action</span></span>  
 <span data-ttu-id="64766-117">지정된 크기의 버퍼를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="64766-117">Provide a buffer of the specified size.</span></span>  
  
  
