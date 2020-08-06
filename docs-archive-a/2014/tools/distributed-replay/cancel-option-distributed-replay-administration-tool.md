---
title: 취소 옵션(Distributed Replay Administration Tool) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
ms.openlocfilehash: d132fbf5ce541a2bdab82e44dc55e6fc92df536d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651954"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a><span data-ttu-id="b5847-102">취소 옵션(Distributed Replay Administration Tool)</span><span class="sxs-lookup"><span data-stu-id="b5847-102">Cancel Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="b5847-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 관리 도구인는 `DReplay.exe` Distributed Replay controller와 통신 하는 데 사용할 수 있는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="b5847-104">이 항목에서는 **cancel** 명령줄 옵션과 해당 구문에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-104">This topic describes the **cancel** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="b5847-105">**cancel** 옵션은 컨트롤러에서 실행 중인 현재 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-105">The **cancel** option cancels the current operation that is running on the controller.</span></span>

 <span data-ttu-id="b5847-106">![항목 링크 아이콘](../../database-engine/media/topic-link.gif "항목 링크 아이콘") 관리 도구 구문에서 사용되는 구문 표기 규칙에 대한 자세한 내용은 [Transact-SQL 구문 표기 규칙&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5847-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="b5847-107">구문</span><span class="sxs-lookup"><span data-stu-id="b5847-107">Syntax</span></span>

```

dreplay cancel [-mcontroller] [-q] 
```

#### <a name="parameters"></a><span data-ttu-id="b5847-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b5847-108">Parameters</span></span>
 <span data-ttu-id="b5847-109">**-m** *컨트롤러* 컨트롤러의 컴퓨터 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-109">**-m** *controller* The computer name of the controller.</span></span> <span data-ttu-id="b5847-110">"`localhost`" 또는 "`.`"을 사용하여 로컬 컴퓨터를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="b5847-111">**-m** 매개 변수를 지정하지 않으면 로컬 컴퓨터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="b5847-112">**-q** 자동 모드.</span><span class="sxs-lookup"><span data-stu-id="b5847-112">**-q** Quiet mode.</span></span> <span data-ttu-id="b5847-113">확인 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-113">Does not prompt for confirmation.</span></span>

 <span data-ttu-id="b5847-114">**-q** 매개 변수는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-114">The **-q** parameter is optional.</span></span>

## <a name="examples"></a><span data-ttu-id="b5847-115">예</span><span class="sxs-lookup"><span data-stu-id="b5847-115">Examples</span></span>
 <span data-ttu-id="b5847-116">다음 예에서는 취소 요청이 자동 모드로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-116">In the following example, a cancel request is submitted in quiet mode.</span></span> <span data-ttu-id="b5847-117">`localhost` 값은 컨트롤러 서비스가 관리 도구와 동일한 컴퓨터에서 실행 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-117">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay cancel -m localhost -q
```

## <a name="permissions"></a><span data-ttu-id="b5847-118">사용 권한</span><span class="sxs-lookup"><span data-stu-id="b5847-118">Permissions</span></span>
 <span data-ttu-id="b5847-119">관리 도구는 로컬 사용자 또는 도메인 사용자 등의 대화형 사용자 계정으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-119">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="b5847-120">로컬 사용자 계정을 사용하려면 관리 도구와 컨트롤러가 동일한 컴퓨터에서 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5847-120">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="b5847-121">자세한 내용은 [Distributed Replay Security](distributed-replay-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5847-121">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5847-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5847-122">See Also</span></span>
 [<span data-ttu-id="b5847-123">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="b5847-123">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)


