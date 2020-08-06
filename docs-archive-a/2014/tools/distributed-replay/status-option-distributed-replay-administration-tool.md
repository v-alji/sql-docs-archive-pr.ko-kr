---
title: 상태 옵션(Distributed Replay Administration Tool) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ce3d07bc357c5f3788fb6f995a43399021b3553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727680"
---
# <a name="status-option-distributed-replay-administration-tool"></a><span data-ttu-id="b7a74-102">상태 옵션(Distributed Replay Administration Tool)</span><span class="sxs-lookup"><span data-stu-id="b7a74-102">Status Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="b7a74-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 관리 도구인는 `DReplay.exe` Distributed Replay controller와 통신 하는 데 사용할 수 있는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="b7a74-104">이 항목에서는 **status** 명령줄 옵션과 해당 구문에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-104">This topic describes the **status** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="b7a74-105">**status** 옵션은 컨트롤러를 쿼리하여 현재 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-105">The **status** option queries the controller and displays the current status.</span></span>

 <span data-ttu-id="b7a74-106">![항목 링크 아이콘](../../database-engine/media/topic-link.gif "항목 링크 아이콘") 관리 도구 구문에서 사용되는 구문 표기 규칙에 대한 자세한 내용은 [Transact-SQL 구문 표기 규칙&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7a74-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="b7a74-107">구문</span><span class="sxs-lookup"><span data-stu-id="b7a74-107">Syntax</span></span>

```

dreplay status [-mcontroller] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="b7a74-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b7a74-108">Parameters</span></span>
 <span data-ttu-id="b7a74-109">**-m** *컨트롤러* 컨트롤러의 컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-109">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="b7a74-110">"`localhost`" 또는 "`.`"을 사용하여 로컬 컴퓨터를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="b7a74-111">**-m** 매개 변수를 지정하지 않으면 로컬 컴퓨터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="b7a74-112">**-f** *status_interval* 상태를 표시할 빈도 (초)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-112">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="b7a74-113">**-f** 매개 변수를 지정하지 않을 경우 기본 간격은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-113">If the **-f** parameter is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="b7a74-114">예</span><span class="sxs-lookup"><span data-stu-id="b7a74-114">Examples</span></span>
 <span data-ttu-id="b7a74-115">다음 예에서는 현재 상태가 60초 간격으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-115">In the following example, the current status is displayed every 60 seconds.</span></span> <span data-ttu-id="b7a74-116">`localhost` 값은 컨트롤러 서비스가 관리 도구와 동일한 컴퓨터에서 실행 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-116">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay status -m localhost -f 60
```

## <a name="permissions"></a><span data-ttu-id="b7a74-117">사용 권한</span><span class="sxs-lookup"><span data-stu-id="b7a74-117">Permissions</span></span>
 <span data-ttu-id="b7a74-118">관리 도구는 로컬 사용자 또는 도메인 사용자 등의 대화형 사용자 계정으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-118">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="b7a74-119">로컬 사용자 계정을 사용하려면 관리 도구와 컨트롤러가 동일한 컴퓨터에서 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a74-119">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="b7a74-120">자세한 내용은 [Distributed Replay Security](distributed-replay-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7a74-120">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7a74-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7a74-121">See Also</span></span>
 <span data-ttu-id="b7a74-122">[Transact-sql 디버거](../../relational-databases/scripting/transact-sql-debugger.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md)</span><span class="sxs-lookup"><span data-stu-id="b7a74-122">[SQL Server Distributed Replay](sql-server-distributed-replay.md) [Transact-SQL Debugger](../../relational-databases/scripting/transact-sql-debugger.md)</span></span>


