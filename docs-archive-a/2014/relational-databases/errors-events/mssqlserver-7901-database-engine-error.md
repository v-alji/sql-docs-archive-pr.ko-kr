---
title: MSSQLSERVER_7901 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fae6e55cbe7170f795aff85400da2c5cdaef780a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651008"
---
# <a name="mssqlserver_7901"></a><span data-ttu-id="8ceda-102">MSSQLSERVER_7901</span><span class="sxs-lookup"><span data-stu-id="8ceda-102">MSSQLSERVER_7901</span></span>
    
## <a name="details"></a><span data-ttu-id="8ceda-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="8ceda-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ceda-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8ceda-104">Product Name</span></span>|<span data-ttu-id="8ceda-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8ceda-105">SQL Server</span></span>|  
|<span data-ttu-id="8ceda-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="8ceda-106">Event ID</span></span>|<span data-ttu-id="8ceda-107">7901</span><span class="sxs-lookup"><span data-stu-id="8ceda-107">7901</span></span>|  
|<span data-ttu-id="8ceda-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="8ceda-108">Event Source</span></span>|<span data-ttu-id="8ceda-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8ceda-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8ceda-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8ceda-110">Component</span></span>|<span data-ttu-id="8ceda-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8ceda-111">SQLEngine</span></span>|  
|<span data-ttu-id="8ceda-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="8ceda-112">Symbolic Name</span></span>|<span data-ttu-id="8ceda-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span><span class="sxs-lookup"><span data-stu-id="8ceda-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span></span>|  
|<span data-ttu-id="8ceda-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="8ceda-114">Message Text</span></span>|<span data-ttu-id="8ceda-115">복구 문이 처리되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8ceda-115">The repair statement was not processed.</span></span> <span data-ttu-id="8ceda-116">데이터베이스가 응급 모드인 경우 이 복구 수준은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ceda-116">This level of repair is not supported when the database is in emergency mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8ceda-117">설명</span><span class="sxs-lookup"><span data-stu-id="8ceda-117">Explanation</span></span>  
 <span data-ttu-id="8ceda-118">데이터베이스가 응급 모드이며 REPAIR_ALLOW_DATA_LOSS 이외의 복구 수준이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ceda-118">The database is in emergency mode and a repair level other than REPAIR_ALLOW_DATA_LOSS has been specified.</span></span> <span data-ttu-id="8ceda-119">REPAIR_ALLOW_DATA_LOSS를 지정하지 않는 한 응급 모드에서는 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ceda-119">Repairs cannot be made in emergency mode unless REPAIR_ALLOW_DATA_LOSS is specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8ceda-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="8ceda-120">User Action</span></span>  
 <span data-ttu-id="8ceda-121">명령을 다시 실행하고 REPAIR_ALLOW_DATA_LOSS 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ceda-121">Rerun the command and specify the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
  
