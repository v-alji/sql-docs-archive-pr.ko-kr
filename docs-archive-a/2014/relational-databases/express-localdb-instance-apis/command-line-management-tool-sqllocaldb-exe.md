---
title: '명령줄 관리 도구: SqlLocalDB.exe | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d21a6a8879e981e52bd2e7d3bd05a37e65d8cf4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647024"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a><span data-ttu-id="595f4-102">명령줄 관리 도구: SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="595f4-102">Command-Line Management Tool: SqlLocalDB.exe</span></span>
  <span data-ttu-id="595f4-103">SqlLocalDB.exe는 사용자가 명령줄에서 LocalDB 인스턴스를 쉽게 관리할 수 있는 간단한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-103">SqlLocalDB.exe is a simple tool that enables the user to easily manage LocalDB instances from the command line.</span></span> <span data-ttu-id="595f4-104">이 도구는 LocalDB 인스턴스 API에 대한 단순 래퍼로 구현되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-104">It is implemented as a simple wrapper around the LocalDB instance API.</span></span> <span data-ttu-id="595f4-105">SQLCMD 등의 비슷한 여러 SQL Server 도구와 마찬가지로 매개 변수는 SqlLocalDB에 명령줄 인수로 전달되며 출력은 콘솔로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-105">As in many similar SQL Server tools (for example, SQLCMD), parameters are passed to SqlLocalDB as command-line arguments and output is sent to the console.</span></span>  
  
 <span data-ttu-id="595f4-106">SqlLocalDB를 사용하면 개발자는 API를 호출하는 코드를 작성할 필요 없이 LocalDB를 사용하거나 다른 도구를 이용하여 자동으로 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-106">SqlLocalDB enables developers to use LocalDB without having to write code to call the API or depend on other tools to do it for them.</span></span>  
  
## <a name="sqllocaldb-options"></a><span data-ttu-id="595f4-107">SqlLocalDB 옵션</span><span class="sxs-lookup"><span data-stu-id="595f4-107">SqlLocalDB Options</span></span>  
 <span data-ttu-id="595f4-108">SqlLocalDB에서는 다음과 같은 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-108">SqlLocalDB supports the following options.</span></span>  
  
|<span data-ttu-id="595f4-109">옵션</span><span class="sxs-lookup"><span data-stu-id="595f4-109">Option</span></span>|<span data-ttu-id="595f4-110">수행하는 작업</span><span class="sxs-lookup"><span data-stu-id="595f4-110">What it does</span></span>|  
|------------|------------------|  
|`-?`|<span data-ttu-id="595f4-111">도움말 텍스트를 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-111">Prints help text.</span></span>|  
|`create&#124;c "instance name" [version-number] [-s]`|<span data-ttu-id="595f4-112">지정한 이름과 버전으로 새 LocalDB 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-112">Creates a new LocalDB instance with a specified name and version.</span></span><br /><br /> <span data-ttu-id="595f4-113">[버전 번호] 매개 변수를 생략하면 기본값으로 SqlLocalDB 빌드 버전이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-113">If the [version-number] parameter is omitted, it defaults to the SqlLocalDB build version.</span></span><br /><br /> <span data-ttu-id="595f4-114">-s는 인스턴스가 만들어진 후 새 LocalDB 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-114">-s starts the new LocalDB instance after it is created.</span></span>|  
|`delete&#124;d "instance name"`|<span data-ttu-id="595f4-115">지정한 이름의 LocalDB 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-115">Deletes the LocalDB instance with the specified name.</span></span>|  
|`start&#124;s "instance name"`|<span data-ttu-id="595f4-116">지정한 이름으로 LocalDB 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-116">Starts the LocalDB instance with the specified name.</span></span>|  
|`stop&#124;p "instance name" [-i&#124;-k]`|<span data-ttu-id="595f4-117">현재 쿼리의 실행을 완료한 후 지정한 이름의 LocalDB 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-117">Stops the LocalDB instance with the specified name, after current queries finish running.</span></span><br /><br /> <span data-ttu-id="595f4-118">-i는 NOWAIT 옵션을 사용하여 LocalDB 인스턴스 종료를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-118">-i requests the LocalDB instance shutdown with the NOWAIT option.</span></span><br /><br /> <span data-ttu-id="595f4-119">-k는 프로세스와 접촉하지 않고 LocalDB 인스턴스 프로세스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-119">-k kills the LocalDB instance process without contacting it.</span></span>|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|<span data-ttu-id="595f4-120">지정한 공유 이름을 사용하여 지정한 프라이빗 인스턴스를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-120">Shares the specified private instance using the specified shared name.</span></span> <span data-ttu-id="595f4-121">사용자 SID 또는 계정 이름을 생략하면 기본값으로 현재 사용자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-121">If the user SID or account name is omitted, it defaults to the current user.</span></span>|  
|`unshare&#124;u "shared name"`|<span data-ttu-id="595f4-122">지정한 공유 LocalDB 인스턴스의 공유를 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-122">Unshares the specified shared LocalDB instance.</span></span>|  
|`info&#124;i`|<span data-ttu-id="595f4-123">현재 사용자가 소유하고 있는 모든 기존 LocalDB 인스턴스와 모든 공유 LocalDB 인스턴스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-123">Lists all existing LocalDB instances that are owned by the current user and all shared LocalDB instances.</span></span>|  
|`info&#124;i "instance name"`|<span data-ttu-id="595f4-124">지정한 LocalDB 인스턴스에 대한 정보를 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-124">Prints the information about the specified LocalDB instance.</span></span>|  
|`versions&#124;v`|<span data-ttu-id="595f4-125">컴퓨터에 설치된 모든 LocalDB 버전을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-125">Lists all LocalDB versions installed on the computer.</span></span>|  
|||  
|`trace&#124;t on&#124;off`|<span data-ttu-id="595f4-126">추적을 설정하고 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-126">Turns tracing on and off.</span></span>|  
  
 <span data-ttu-id="595f4-127">SqlLocalDB에서는 공백을 구분 기호로 처리하므로 공백 및 공백 문자가 포함된 인스턴스 이름은 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-127">SqlLocalDB treats spaces as delimiters; you must surround the instance names that contain spaces and special characters with quotes.</span></span> <span data-ttu-id="595f4-128">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="595f4-128">For example:</span></span>  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
