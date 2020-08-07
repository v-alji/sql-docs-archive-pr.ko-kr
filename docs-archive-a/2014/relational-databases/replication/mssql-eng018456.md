---
title: MSSQL_ENG018456 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b05ca549781215e0c4f247110fee87f6def56f04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733955"
---
# <a name="mssql_eng018456"></a><span data-ttu-id="53a05-102">MSSQL_ENG018456</span><span class="sxs-lookup"><span data-stu-id="53a05-102">MSSQL_ENG018456</span></span>
    
## <a name="message-details"></a><span data-ttu-id="53a05-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="53a05-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53a05-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="53a05-104">Product Name</span></span>|<span data-ttu-id="53a05-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="53a05-105">SQL Server</span></span>|  
|<span data-ttu-id="53a05-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="53a05-106">Event ID</span></span>|<span data-ttu-id="53a05-107">18456</span><span class="sxs-lookup"><span data-stu-id="53a05-107">18456</span></span>|  
|<span data-ttu-id="53a05-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="53a05-108">Event Source</span></span>|<span data-ttu-id="53a05-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="53a05-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="53a05-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="53a05-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="53a05-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="53a05-111">Symbolic Name</span></span>||  
|<span data-ttu-id="53a05-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="53a05-112">Message Text</span></span>|<span data-ttu-id="53a05-113">사용자 '%.\*ls'이(가) 로그인하지 못했습니다.%.\*ls</span><span class="sxs-lookup"><span data-stu-id="53a05-113">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="53a05-114">설명</span><span class="sxs-lookup"><span data-stu-id="53a05-114">Explanation</span></span>  
 <span data-ttu-id="53a05-115">로그인 시도가 실패할 때마다 MSSQL_ENG018456 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="53a05-115">Error MSSQL_ENG018456 is raised whenever a login attempt fails.</span></span> <span data-ttu-id="53a05-116">오류 메시지에 **distributor_admin** 계정이 포함된 경우(사용자 'distributor_admin'이 로그인하지 못했습니다 등) 복제에 사용된 계정에 문제가 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="53a05-116">If the error message includes the account **distributor_admin** (Login failed for user 'distributor_admin'.), the issue is with an account used by replication.</span></span> <span data-ttu-id="53a05-117">복제는 원격 서버 **repl_distributor**를 만들어 배포자와 게시자 간 통신을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="53a05-117">Replication creates a remote server, **repl_distributor**, which allows communication between the Distributor and Publisher.</span></span> <span data-ttu-id="53a05-118">로그인 **distributor_admin** 은 이 원격 서버와 연결되며 유효한 암호가 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53a05-118">The login **distributor_admin** is associated with this remote server and must have a valid password.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53a05-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="53a05-119">User Action</span></span>  
 <span data-ttu-id="53a05-120">이 계정의 암호를 지정했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="53a05-120">Ensure that you have specified a password for this account.</span></span> <span data-ttu-id="53a05-121">자세한 내용은 [배포자 보안 설정](security/secure-the-distributor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53a05-121">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53a05-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53a05-122">See Also</span></span>  
 [<span data-ttu-id="53a05-123">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="53a05-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
