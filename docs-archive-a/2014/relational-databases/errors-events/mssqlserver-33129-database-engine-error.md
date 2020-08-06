---
title: MSSQLSERVER_33129 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da7735889dce8bfc33e624115e8245f8a02f46b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650053"
---
# <a name="mssqlserver_33129"></a><span data-ttu-id="c9a7b-102">MSSQLSERVER_33129</span><span class="sxs-lookup"><span data-stu-id="c9a7b-102">MSSQLSERVER_33129</span></span>
    
## <a name="details"></a><span data-ttu-id="c9a7b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c9a7b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9a7b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c9a7b-104">Product Name</span></span>|<span data-ttu-id="c9a7b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c9a7b-105">SQL Server</span></span>|  
|<span data-ttu-id="c9a7b-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c9a7b-106">Event ID</span></span>|<span data-ttu-id="c9a7b-107">33129</span><span class="sxs-lookup"><span data-stu-id="c9a7b-107">33129</span></span>|  
|<span data-ttu-id="c9a7b-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c9a7b-108">Event Source</span></span>|<span data-ttu-id="c9a7b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c9a7b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c9a7b-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c9a7b-110">Component</span></span>|<span data-ttu-id="c9a7b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c9a7b-111">SQLEngine</span></span>|  
|<span data-ttu-id="c9a7b-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c9a7b-112">Symbolic Name</span></span>|<span data-ttu-id="c9a7b-113">SEC_CANNOT_DISABLE_WIN_GROUP</span><span class="sxs-lookup"><span data-stu-id="c9a7b-113">SEC_CANNOT_DISABLE_WIN_GROUP</span></span>|  
|<span data-ttu-id="c9a7b-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c9a7b-114">Message Text</span></span>|<span data-ttu-id="c9a7b-115">ALTER_LOGIN에 DISABLE 인수를 사용하여 Windows 그룹에 대한 액세스를 거부할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a7b-115">Cannot use ALTER_LOGIN with the DISABLE argument to deny access to a Windows group.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c9a7b-116">설명</span><span class="sxs-lookup"><span data-stu-id="c9a7b-116">Explanation</span></span>  
 <span data-ttu-id="c9a7b-117">이 메시지는 Windows 그룹의 로그인을 사용하지 않도록 설정할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a7b-117">This message occurs when attempting to disable the login of a Windows Group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c9a7b-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c9a7b-118">User Action</span></span>  
 <span data-ttu-id="c9a7b-119">Windows 그룹의 로그인은 사용하지 않도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a7b-119">The login of a Windows Group cannot be disabled.</span></span> <span data-ttu-id="c9a7b-120">Windows 그룹에 부여된 액세스 권한을 임시로 제거하려면 Windows 그룹의 로그인에 대한 CONNECT 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a7b-120">To temporarily remove access permission granted to a Windows Group, REVOKE the CONNECT permission of the login for the Windows Group.</span></span> <span data-ttu-id="c9a7b-121">그래도 Windows 사용자는 자신의 개별 로그인이나 다른 Windows 그룹을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a7b-121">Windows users might still have access through their individual login or through another Windows Group.</span></span> <span data-ttu-id="c9a7b-122">다음 예에서는 WESTCOAST 도메인의 Accounting 그룹에 대한 연결 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a7b-122">The following example revokes the connect permission to the Accounting Group of the WESTCOAST domain.</span></span>  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
