---
title: MSSQLSERVER_3937 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac466e6eb50ad4b7a8848a1159963cb0fd35e22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731627"
---
# <a name="mssqlserver_3937"></a><span data-ttu-id="374e3-102">MSSQLSERVER_3937</span><span class="sxs-lookup"><span data-stu-id="374e3-102">MSSQLSERVER_3937</span></span>
    
## <a name="details"></a><span data-ttu-id="374e3-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="374e3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="374e3-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="374e3-104">Product Name</span></span>|<span data-ttu-id="374e3-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="374e3-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="374e3-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="374e3-106">Event ID</span></span>|<span data-ttu-id="374e3-107">3937</span><span class="sxs-lookup"><span data-stu-id="374e3-107">3937</span></span>|  
|<span data-ttu-id="374e3-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="374e3-108">Event Source</span></span>|<span data-ttu-id="374e3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="374e3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="374e3-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="374e3-110">Component</span></span>|<span data-ttu-id="374e3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="374e3-111">SQLEngine</span></span>|  
|<span data-ttu-id="374e3-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="374e3-112">Symbolic Name</span></span>|<span data-ttu-id="374e3-113">XACT_FILESTREAM_ROLLBACK_ERROR</span><span class="sxs-lookup"><span data-stu-id="374e3-113">XACT_FILESTREAM_ROLLBACK_ERROR</span></span>|  
|<span data-ttu-id="374e3-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="374e3-114">Message Text</span></span>|<span data-ttu-id="374e3-115">FILESTREAM 필터 드라이버로 트랜잭션이 롤백되었음을 알리는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="374e3-115">An error occurred while trying to notify the FILESTREAM filter driver that a transaction was rolled back.</span></span> <span data-ttu-id="374e3-116">오류 코드: 0x%0x.</span><span class="sxs-lookup"><span data-stu-id="374e3-116">Error code: 0x%0x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="374e3-117">설명</span><span class="sxs-lookup"><span data-stu-id="374e3-117">Explanation</span></span>  
 <span data-ttu-id="374e3-118">트랜잭션에 대한 롤백 알림을 실행하는 동안 RsFx 드라이버에서 오류가 반환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="374e3-118">An error was returned by the RsFx driver when issuing a rollback notification for a transaction.</span></span> <span data-ttu-id="374e3-119">이 오류는 리소스 부족으로 인해 발생한 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="374e3-119">This is probably caused by a resource shortage.</span></span> <span data-ttu-id="374e3-120">이로 인해 RsFx 필터 드라이버에서 약간의 메모리 누수가 발생할 수 있습니다. 하지만 트랜잭션을 만든 sqlservr.exe 프로세스가 종료되면 이 문제는 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="374e3-120">This can cause a small memory leak in the RsFx filter driver, but this will be freed when the sqlservr.exe process that created the transaction exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="374e3-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="374e3-121">User Action</span></span>  
  
