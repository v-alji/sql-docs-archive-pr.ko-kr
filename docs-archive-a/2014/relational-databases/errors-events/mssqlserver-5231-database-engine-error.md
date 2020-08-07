---
title: MSSQLSERVER_5231 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 68f40ac3a566280526757bd8b83c784954ba3dde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729503"
---
# <a name="mssqlserver_5231"></a><span data-ttu-id="795b1-102">MSSQLSERVER_5231</span><span class="sxs-lookup"><span data-stu-id="795b1-102">MSSQLSERVER_5231</span></span>
    
## <a name="details"></a><span data-ttu-id="795b1-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="795b1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="795b1-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="795b1-104">Product Name</span></span>|<span data-ttu-id="795b1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="795b1-105">SQL Server</span></span>|  
|<span data-ttu-id="795b1-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="795b1-106">Event ID</span></span>|<span data-ttu-id="795b1-107">5231</span><span class="sxs-lookup"><span data-stu-id="795b1-107">5231</span></span>|  
|<span data-ttu-id="795b1-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="795b1-108">Event Source</span></span>|<span data-ttu-id="795b1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="795b1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="795b1-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="795b1-110">Component</span></span>|<span data-ttu-id="795b1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="795b1-111">SQLEngine</span></span>|  
|<span data-ttu-id="795b1-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="795b1-112">Symbolic Name</span></span>|<span data-ttu-id="795b1-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span><span class="sxs-lookup"><span data-stu-id="795b1-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span></span>|  
|<span data-ttu-id="795b1-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="795b1-114">Message Text</span></span>|<span data-ttu-id="795b1-115">개체 ID O_ID(개체 'NAME'): 확인을 위해 이 개체를 잠그는 동안 교착 상태가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="795b1-115">Object ID O_ID (object 'NAME'): A deadlock occurred while trying to lock this object for checking.</span></span> <span data-ttu-id="795b1-116">이 개체를 건너뛰었으므로 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="795b1-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="795b1-117">설명</span><span class="sxs-lookup"><span data-stu-id="795b1-117">Explanation</span></span>  
 <span data-ttu-id="795b1-118">DBCC가 개체를 잠그려고 할 때 교착 상태가 발생하여 DBCC 실행이 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="795b1-118">A deadlock occurred when DBCC was trying to lock the object, and DBCC was chosen as the deadlock victim.</span></span> <span data-ttu-id="795b1-119">개체가 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="795b1-119">The object will not be processed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="795b1-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="795b1-120">User Action</span></span>  
 <span data-ttu-id="795b1-121">None</span><span class="sxs-lookup"><span data-stu-id="795b1-121">None</span></span>  
  
  
