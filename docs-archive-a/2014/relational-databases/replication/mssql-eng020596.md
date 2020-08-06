---
title: MSSQL_ENG020596 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b1c61f3683442e0d474ff36a65c89446dbd7bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661048"
---
# <a name="mssql_eng020596"></a><span data-ttu-id="97c75-102">MSSQL_ENG020596</span><span class="sxs-lookup"><span data-stu-id="97c75-102">MSSQL_ENG020596</span></span>
    
## <a name="message-details"></a><span data-ttu-id="97c75-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="97c75-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97c75-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="97c75-104">Product Name</span></span>|<span data-ttu-id="97c75-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="97c75-105">SQL Server</span></span>|  
|<span data-ttu-id="97c75-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="97c75-106">Event ID</span></span>|<span data-ttu-id="97c75-107">20596</span><span class="sxs-lookup"><span data-stu-id="97c75-107">20596</span></span>|  
|<span data-ttu-id="97c75-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="97c75-108">Event Source</span></span>|<span data-ttu-id="97c75-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="97c75-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="97c75-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="97c75-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="97c75-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="97c75-111">Symbolic Name</span></span>||  
|<span data-ttu-id="97c75-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="97c75-112">Message Text</span></span>|<span data-ttu-id="97c75-113">'%s' 또는 db_owner의 멤버만 익명 에이전트를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97c75-113">Only '%s' or members of db_owner can drop the anonymous agent.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="97c75-114">설명</span><span class="sxs-lookup"><span data-stu-id="97c75-114">Explanation</span></span>  
 <span data-ttu-id="97c75-115">익명 구독에 대한 에이전트를 삭제할 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97c75-115">You do not have sufficient permissions to drop the agent for the anonymous subscription.</span></span> <span data-ttu-id="97c75-116">[sp_dropanonymousagent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql)를 호출할 때 사용된 로그인은 배포자의 **sysadmin** 고정 서버 역할의 멤버이거나 배포 데이터베이스의 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다. 또는 사용자가 에이전트를 처음 실행한 사용자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97c75-116">The login used when calling [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) must be a member of the **sysadmin** fixed server role at the Distributor or **db_owner** fixed database role in the distribution database, or the user must be the one that initiated the first run of the agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="97c75-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="97c75-117">User Action</span></span>  
 <span data-ttu-id="97c75-118">올바른 자격 증명으로 로그인하고 **sp_dropanonymousagent**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="97c75-118">Login with the appropriate credentials, and execute **sp_dropanonymousagent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c75-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97c75-119">See Also</span></span>  
 [<span data-ttu-id="97c75-120">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="97c75-120">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
