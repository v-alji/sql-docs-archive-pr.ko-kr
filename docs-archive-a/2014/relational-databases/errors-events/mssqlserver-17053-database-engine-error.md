---
title: MSSQLSERVER_17053 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11137ba334b66f20c7d9a6caaaf7d1ef42c15dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638813"
---
# <a name="mssqlserver_17053"></a><span data-ttu-id="ee324-102">MSSQLSERVER_17053</span><span class="sxs-lookup"><span data-stu-id="ee324-102">MSSQLSERVER_17053</span></span>
    
## <a name="details"></a><span data-ttu-id="ee324-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ee324-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee324-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ee324-104">Product Name</span></span>|<span data-ttu-id="ee324-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ee324-105">SQL Server</span></span>|  
|<span data-ttu-id="ee324-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ee324-106">Event ID</span></span>|<span data-ttu-id="ee324-107">17053</span><span class="sxs-lookup"><span data-stu-id="ee324-107">17053</span></span>|  
|<span data-ttu-id="ee324-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ee324-108">Event Source</span></span>|<span data-ttu-id="ee324-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ee324-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ee324-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ee324-110">Component</span></span>|<span data-ttu-id="ee324-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ee324-111">SQLEngine</span></span>|  
|<span data-ttu-id="ee324-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ee324-112">Symbolic Name</span></span>|<span data-ttu-id="ee324-113">OS_ERROR</span><span class="sxs-lookup"><span data-stu-id="ee324-113">OS_ERROR</span></span>|  
|<span data-ttu-id="ee324-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ee324-114">Message Text</span></span>|<span data-ttu-id="ee324-115">%ls: 운영 체제 오류 %ls이(가) 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ee324-115">%ls: Operating system error %ls encountered.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee324-116">설명</span><span class="sxs-lookup"><span data-stu-id="ee324-116">Explanation</span></span>  
 <span data-ttu-id="ee324-117">일반적인 운영 체제 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ee324-117">Generic operating system error occurred.</span></span>  <span data-ttu-id="ee324-118">결과 상태가 분명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee324-118">Not clear what the resulting state is.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee324-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ee324-119">User Action</span></span>  
 <span data-ttu-id="ee324-120">일반적으로 이 오류는 다른 오류와 함께 발생하며 해당 오류를 진단하는 데 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee324-120">Usually this is in conjunction with some other error and should be used to help diagnose that failure.</span></span> <span data-ttu-id="ee324-121">이러한 오류의 예로는 데이터 또는 로그 파일 읽기/쓰기 실패, 레지스트리 읽기/쓰기 작업, 예기치 않은 Win32API 오류 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee324-121">Examples would include reads or writes to data or log files that fail, registry read/write operations, or other unexpected Win32API failures.</span></span>  
  
  
