---
title: SqlLocalDB 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfb95cea4365d56c296d14fcc09046cd7eddc0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727556"
---
# <a name="sqllocaldb-utility"></a><span data-ttu-id="e8f08-102">SqlLocalDB 유틸리티</span><span class="sxs-lookup"><span data-stu-id="e8f08-102">SqlLocalDB Utility</span></span>
  <span data-ttu-id="e8f08-103">유틸리티를 사용 `SqlLocalDB` 하 여 LocalDB의 인스턴스를 만듭니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB**.</span><span class="sxs-lookup"><span data-stu-id="e8f08-103">Use the `SqlLocalDB` utility to create an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)]**LocalDB**.</span></span> <span data-ttu-id="e8f08-104">`SqlLocalDB`유틸리티 (SqlLocalDB.exe)는 사용자와 개발자가 LocalDB의 인스턴스를 만들고 관리 하는 데 사용할 수 있는 간단한 명령줄 도구입니다 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**.</span><span class="sxs-lookup"><span data-stu-id="e8f08-104">The `SqlLocalDB` utility (SqlLocalDB.exe) is a simple command line tool to enable users and developers to create and manage an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="e8f08-105">**Localdb**를 사용 하는 방법에 대 한 자세한 내용은 [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f08-105">For information about how to use **LocalDB**, see [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f08-106">구문</span><span class="sxs-lookup"><span data-stu-id="e8f08-106">Syntax</span></span>  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8f08-107">인수</span><span class="sxs-lookup"><span data-stu-id="e8f08-107">Arguments</span></span>  
 <span data-ttu-id="e8f08-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* [ **-s** ]</span><span class="sxs-lookup"><span data-stu-id="e8f08-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* [**-s** ]</span></span>  
 <span data-ttu-id="e8f08-109">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-109">Creates a new of instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="e8f08-110">`SqlLocalDB`는 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] 인수로 지정 된 이진 파일의 버전을 사용 *\<instance-version>* 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-110">`SqlLocalDB` uses the version of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] binaries specified by *\<instance-version>* argument.</span></span> <span data-ttu-id="e8f08-111">버전 번호는 하나 이상의 숫자를 포함하는 숫자 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-111">The version number is specified in numeric format with at least one decimal.</span></span> <span data-ttu-id="e8f08-112">부 버전 번호(서비스 팩)는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-112">The minor version numbers (service packs) are optional.</span></span> <span data-ttu-id="e8f08-113">예를 들어 버전 번호 11.0 또는 11.0.1186은 모두 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-113">For example the following two version numbers are both acceptable: 11.0, or 11.0.1186.</span></span> <span data-ttu-id="e8f08-114">지정된 버전을 컴퓨터에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-114">The specified version must be installed on the computer.</span></span> <span data-ttu-id="e8f08-115">지정 하지 않으면 버전 번호는 기본적으로 유틸리티 버전으로 지정 `SqlLocalDB` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-115">If not specified, the version number defaults to the version of the `SqlLocalDB` utility.</span></span> <span data-ttu-id="e8f08-116">**–s**를 추가하여 **LocalDB**의 새 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-116">Adding **-s** starts the new instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="e8f08-117">[ **share** | **h** ]</span><span class="sxs-lookup"><span data-stu-id="e8f08-117">[ **share** | **h** ]</span></span>  
 <span data-ttu-id="e8f08-118">지정한 공유 이름을 사용하여 지정한 프라이빗 **LocalDB** 인스턴스를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-118">Shares the specified private instance of **LocalDB** using the specified shared name.</span></span> <span data-ttu-id="e8f08-119">사용자 SID 또는 계정 이름을 생략하면 기본값으로 현재 사용자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-119">If the user SID or account name is omitted, it defaults to the current user.</span></span>  
  
 <span data-ttu-id="e8f08-120">[ **unshared** | **u** ]</span><span class="sxs-lookup"><span data-stu-id="e8f08-120">[ **unshared** | **u** ]</span></span>  
 <span data-ttu-id="e8f08-121">**LocalDB**의 지정된 공유 인스턴스의 공유를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-121">Stops the sharing of the specified shared instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="e8f08-122">[ **delete** | **d** ] *\<instance-name>*</span><span class="sxs-lookup"><span data-stu-id="e8f08-122">[ **delete** | **d** ] *\<instance-name>*</span></span>  
 <span data-ttu-id="e8f08-123">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**의 지정된 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-123">Deletes the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span>  
  
 <span data-ttu-id="e8f08-124">[ **start** | **s** ] " *\<instance-name>* "</span><span class="sxs-lookup"><span data-stu-id="e8f08-124">[ **start** | **s** ] "*\<instance-name>*"</span></span>  
 <span data-ttu-id="e8f08-125">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**의 지정된 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-125">Starts the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="e8f08-126">성공하면 문이 **LocalDB**의 명명된 파이프 주소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-126">When successful the statement returns the named pipe address of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="e8f08-127">[ **stop** | **p** ] *\<instance-name>* [ **-i** ] [ **-k** ]</span><span class="sxs-lookup"><span data-stu-id="e8f08-127">[ **stop** | **p** ] *\<instance-name>* [**-i** ] [**-k** ]</span></span>  
 <span data-ttu-id="e8f08-128">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**의 지정된 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-128">Stops the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="e8f08-129">**-I** 를 추가 하면 옵션을 사용 하 여 인스턴스 종료를 요청 합니다 `NOWAIT` .</span><span class="sxs-lookup"><span data-stu-id="e8f08-129">Adding **-i** requests the instance shutdown with the `NOWAIT` option.</span></span> <span data-ttu-id="e8f08-130">**–k**를 추가하면 인스턴스 프로세스에 연결하지 않고 해당 프로세스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-130">Adding **-k** kills the instance process without contacting it.</span></span>  
  
 <span data-ttu-id="e8f08-131">[ **info** | **i** ] [ *\<instance-name>* ]</span><span class="sxs-lookup"><span data-stu-id="e8f08-131">[ **info** | **i** ] [ *\<instance-name>* ]</span></span>  
 <span data-ttu-id="e8f08-132">현재 사용자가 소유한 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 의 모든 인스턴스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-132">Lists all instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** owned by the current user.</span></span>  
  
 <span data-ttu-id="e8f08-133">*\<instance-name>* 은 지정된 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 인스턴스의 이름, 버전, 상태(실행 중 또는 중지됨), 마지막 시작 시간 및 **LocalDB**의 로컬 파이프 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-133">*\<instance-name>* returns the name, version, state (Running or Stopped), last start time for the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**, and the local pipe name of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="e8f08-134">[ **trace** | **t** ] **on** | **off**</span><span class="sxs-lookup"><span data-stu-id="e8f08-134">[ **trace** | **t** ] **on** | **off**</span></span>  
 <span data-ttu-id="e8f08-135">**trace on** 을 사용 하면 `SqlLocalDB` 현재 사용자에 대 한 API 호출을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-135">**trace on** enables tracing for the `SqlLocalDB` API calls for the current user.</span></span> <span data-ttu-id="e8f08-136">**trace off** 를 사용하면 추적이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-136">**trace off** disables tracing.</span></span>  
  
 <span data-ttu-id="e8f08-137">**-?**</span><span class="sxs-lookup"><span data-stu-id="e8f08-137">**-?**</span></span>  
 <span data-ttu-id="e8f08-138">각 옵션에 대 한 간략 한 설명을 반환 `SqlLocalDB` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-138">Returns brief descriptions of each `SqlLocalDB` option.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8f08-139">설명</span><span class="sxs-lookup"><span data-stu-id="e8f08-139">Remarks</span></span>  
 <span data-ttu-id="e8f08-140">*instance name* 인수는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자에 대한 규칙을 따르거나 큰따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-140">The *instance name* argument must follow the rules for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers or it must be enclosed in double quotes.</span></span>  
  
 <span data-ttu-id="e8f08-141">인수 없이 SqlLocalDB를 실행하면 도움말 텍스트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-141">Executing SqlLocalDB without arguments returns the help text.</span></span>  
  
 <span data-ttu-id="e8f08-142">시작 이외의 작업은 현재 로그인한 사용자에 속하는 인스턴스에 대해서만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-142">Operations other than start can only be performed on an instance belonging to currently logged in user.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e8f08-143">예</span><span class="sxs-lookup"><span data-stu-id="e8f08-143">Examples</span></span>  
  
### <a name="a-creating-an-instance-of-localdb"></a><span data-ttu-id="e8f08-144">A.</span><span class="sxs-lookup"><span data-stu-id="e8f08-144">A.</span></span> <span data-ttu-id="e8f08-145">LocalDB의 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="e8f08-145">Creating an Instance of LocalDB</span></span>  
 <span data-ttu-id="e8f08-146">다음 예에서는 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**바이너리를 사용하여** 라는 `DEPARTMENT` LocalDB [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 의 인스턴스를 만든 다음 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-146">The following example creates an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** named `DEPARTMENT` using the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] binaries and starts the instance.</span></span>  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a><span data-ttu-id="e8f08-147">B.</span><span class="sxs-lookup"><span data-stu-id="e8f08-147">B.</span></span> <span data-ttu-id="e8f08-148">LocalDB의 공유 인스턴스 작업</span><span class="sxs-lookup"><span data-stu-id="e8f08-148">Working with a Shared Instance of LocalDB</span></span>  
 <span data-ttu-id="e8f08-149">관리자 권한을 사용하여 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-149">Open a command prompt using Administrator privileges.</span></span>  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 <span data-ttu-id="e8f08-150">다음 코드를 실행해서 **로그인을 사용하여** LocalDB `NewLogin` 의 공유 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f08-150">Execute the following code to connect to the shared instance of **LocalDB** using the `NewLogin` login.</span></span>  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8f08-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8f08-151">See Also</span></span>  
 [<span data-ttu-id="e8f08-152">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="e8f08-152">SQL Server 2014 Express LocalDB</span></span>](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
