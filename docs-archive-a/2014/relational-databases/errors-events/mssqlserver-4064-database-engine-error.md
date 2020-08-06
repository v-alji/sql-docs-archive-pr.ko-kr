---
title: MSSQLSERVER_4064 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 201098aadeb6bd091f0312532138f692ae8079b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659979"
---
# <a name="mssqlserver_4064"></a><span data-ttu-id="cd813-102">MSSQLSERVER_4064</span><span class="sxs-lookup"><span data-stu-id="cd813-102">MSSQLSERVER_4064</span></span>
    
## <a name="details"></a><span data-ttu-id="cd813-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="cd813-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd813-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="cd813-104">Product Name</span></span>|<span data-ttu-id="cd813-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cd813-105">SQL Server</span></span>|  
|<span data-ttu-id="cd813-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="cd813-106">Event ID</span></span>|<span data-ttu-id="cd813-107">4064</span><span class="sxs-lookup"><span data-stu-id="cd813-107">4064</span></span>|  
|<span data-ttu-id="cd813-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="cd813-108">Event Source</span></span>|<span data-ttu-id="cd813-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cd813-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cd813-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="cd813-110">Component</span></span>|<span data-ttu-id="cd813-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cd813-111">SQLEngine</span></span>|  
|<span data-ttu-id="cd813-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="cd813-112">Symbolic Name</span></span>|<span data-ttu-id="cd813-113">DB_UFAIL_FATAL</span><span class="sxs-lookup"><span data-stu-id="cd813-113">DB_UFAIL_FATAL</span></span>|  
|<span data-ttu-id="cd813-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="cd813-114">Message Text</span></span>|<span data-ttu-id="cd813-115">사용자 기본 데이터베이스를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd813-115">Cannot open user default database.</span></span> <span data-ttu-id="cd813-116">로그인이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd813-116">Login failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cd813-117">설명</span><span class="sxs-lookup"><span data-stu-id="cd813-117">Explanation</span></span>  
 <span data-ttu-id="cd813-118">SQL Server 로그인의 기본 데이터베이스 문제로 인해 로그인 시 연결하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd813-118">The SQL Server login was unable to connect because of a problem with its default database.</span></span> <span data-ttu-id="cd813-119">데이터베이스 자체가 잘못되었거나 로그인에 데이터베이스에 대한 CONNECT 권한이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="cd813-119">Either the database itself is invalid or the login lacks CONNECT permission on the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd813-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="cd813-120">User Action</span></span>  
 <span data-ttu-id="cd813-121">ALTER LOGIN을 사용하여 로그인의 기본 데이터베이스를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cd813-121">Use ALTER LOGIN to change the login's default database.</span></span> <span data-ttu-id="cd813-122">로그인에 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="cd813-122">Grant CONNECT permission to the login.</span></span>  
  
  
