---
title: MSSQLSERVER_3619 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2328ee6366d47130a02c444bce65b7b655af7965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653887"
---
# <a name="mssqlserver_3619"></a><span data-ttu-id="eea1c-102">MSSQLSERVER_3619</span><span class="sxs-lookup"><span data-stu-id="eea1c-102">MSSQLSERVER_3619</span></span>
    
## <a name="details"></a><span data-ttu-id="eea1c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="eea1c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eea1c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="eea1c-104">Product Name</span></span>|<span data-ttu-id="eea1c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="eea1c-105">SQL Server</span></span>|  
|<span data-ttu-id="eea1c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="eea1c-106">Event ID</span></span>|<span data-ttu-id="eea1c-107">3619</span><span class="sxs-lookup"><span data-stu-id="eea1c-107">3619</span></span>|  
|<span data-ttu-id="eea1c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="eea1c-108">Event Source</span></span>|<span data-ttu-id="eea1c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="eea1c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="eea1c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="eea1c-110">Component</span></span>|<span data-ttu-id="eea1c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="eea1c-111">SQLEngine</span></span>|  
|<span data-ttu-id="eea1c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="eea1c-112">Symbolic Name</span></span>|<span data-ttu-id="eea1c-113">SYS_NOLOG</span><span class="sxs-lookup"><span data-stu-id="eea1c-113">SYS_NOLOG</span></span>|  
|<span data-ttu-id="eea1c-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="eea1c-114">Message Text</span></span>|<span data-ttu-id="eea1c-115">로그 공간이 부족하여 데이터베이스 ID %d에 검사점 레코드를 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eea1c-115">Could not write a checkpoint record in database ID %d because the log is out of space.</span></span> <span data-ttu-id="eea1c-116">데이터베이스 관리자에게 문의하여 로그를 자르거나 데이터베이스 로그 파일에 더 많은 공간을 할당하십시오.</span><span class="sxs-lookup"><span data-stu-id="eea1c-116">Contact the database administrator to truncate the log or allocate more space to the database log files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eea1c-117">설명</span><span class="sxs-lookup"><span data-stu-id="eea1c-117">Explanation</span></span>  
 <span data-ttu-id="eea1c-118">트랜잭션 로그에 필요한 디스크 공간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="eea1c-118">The transaction log is out of disk space.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eea1c-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="eea1c-119">User Action</span></span>  
 <span data-ttu-id="eea1c-120">로그를 잘라 일부 공간을 확보하거나 로그에 더 많은 공간을 할당하십시오.</span><span class="sxs-lookup"><span data-stu-id="eea1c-120">Truncate the log to release some space, or allocate more space to the log.</span></span> <span data-ttu-id="eea1c-121">자세한 내용은 Server SQL 온라인 설명서의 "꽉 찬 트랜잭션 로그 문제 해결(오류 9002)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eea1c-121">For more information see, "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
  
