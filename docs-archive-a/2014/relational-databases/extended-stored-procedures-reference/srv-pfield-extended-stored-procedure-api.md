---
title: srv_pfield(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfield
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfield
ms.assetid: a61e4c1f-e65b-48ea-a7d1-3e1544af389d
author: rothja
ms.author: jroth
ms.openlocfilehash: 90680d59dbf36ad3f713fd7a09d07553890a8668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742120"
---
# <a name="srv_pfield-extended-stored-procedure-api"></a><span data-ttu-id="83d5d-102">srv_pfield(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="83d5d-102">srv_pfield (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="83d5d-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="83d5d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="83d5d-104">데이터베이스 연결에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-104">Returns information about a database connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d5d-105">구문</span><span class="sxs-lookup"><span data-stu-id="83d5d-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_pfield (  
SRV_PROC *  
srvproc  
,  
int   
field  
,  
int *  
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="83d5d-106">인수</span><span class="sxs-lookup"><span data-stu-id="83d5d-106">Arguments</span></span>  
 <span data-ttu-id="83d5d-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="83d5d-107">*srvproc*</span></span>  
 <span data-ttu-id="83d5d-108">데이터베이스 연결을 식별하는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-108">Pointer identifying a database connection.</span></span>  
  
 <span data-ttu-id="83d5d-109">*필드가*</span><span class="sxs-lookup"><span data-stu-id="83d5d-109">*field*</span></span>  
 <span data-ttu-id="83d5d-110">반환할 연결 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-110">Specifies data on the connection to return.</span></span>  
  
|<span data-ttu-id="83d5d-111">값</span><span class="sxs-lookup"><span data-stu-id="83d5d-111">Value</span></span>|<span data-ttu-id="83d5d-112">반환</span><span class="sxs-lookup"><span data-stu-id="83d5d-112">Returns</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="83d5d-113">SRV_APPLNAME</span><span class="sxs-lookup"><span data-stu-id="83d5d-113">SRV_APPLNAME</span></span>|<span data-ttu-id="83d5d-114">연결을 설정할 때 클라이언트가 제공한 애플리케이션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-114">The application name provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="83d5d-115">SRV_BCPFLAG</span><span class="sxs-lookup"><span data-stu-id="83d5d-115">SRV_BCPFLAG</span></span>|<span data-ttu-id="83d5d-116">플래그로, 클라이언트가 대량 복사 작업을 준비 중이면 TRUE이고, 그렇지 않으면 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-116">A flag that is TRUE if the client is preparing for a bulk copy operation; otherwise, FALSE.</span></span>|  
|<span data-ttu-id="83d5d-117">SRV_CLIB</span><span class="sxs-lookup"><span data-stu-id="83d5d-117">SRV_CLIB</span></span>|<span data-ttu-id="83d5d-118">클라이언트에서 서버로의 통신을 가능하게 하는 라이브러리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-118">The name of the library that enables the client to talk to a server.</span></span>|  
|<span data-ttu-id="83d5d-119">SRV_CPID</span><span class="sxs-lookup"><span data-stu-id="83d5d-119">SRV_CPID</span></span>|<span data-ttu-id="83d5d-120">클라이언트 원본 컴퓨터의 클라이언트 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-120">The client process ID on the client source computer.</span></span>|  
|<span data-ttu-id="83d5d-121">SRV_HOST</span><span class="sxs-lookup"><span data-stu-id="83d5d-121">SRV_HOST</span></span>|<span data-ttu-id="83d5d-122">연결을 설정할 때 클라이언트가 제공한 클라이언트 컴퓨터 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-122">The name of the client's machine provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="83d5d-123">SRV_LIBVERS</span><span class="sxs-lookup"><span data-stu-id="83d5d-123">SRV_LIBVERS</span></span>|<span data-ttu-id="83d5d-124">클라이언트 라이브러리의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-124">The version of the client library.</span></span>|  
|<span data-ttu-id="83d5d-125">SRV_LSECURE</span><span class="sxs-lookup"><span data-stu-id="83d5d-125">SRV_LSECURE</span></span>|<span data-ttu-id="83d5d-126">플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-126">A flag.</span></span> <span data-ttu-id="83d5d-127">연결에서 통합 보안을 사용하여 로그인한 경우 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-127">TRUE if the connection used integrated security to login.</span></span>|  
|<span data-ttu-id="83d5d-128">SRV_NETWORK_MODULE</span><span class="sxs-lookup"><span data-stu-id="83d5d-128">SRV_NETWORK_MODULE</span></span>|<span data-ttu-id="83d5d-129">연결에서 사용하는 네트워크 라이브러리 DLL의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-129">The name of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="83d5d-130">SRV_NETWORK_VERSION</span><span class="sxs-lookup"><span data-stu-id="83d5d-130">SRV_NETWORK_VERSION</span></span>|<span data-ttu-id="83d5d-131">연결에서 사용하는 네트워크 라이브러리 DLL의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-131">The version of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="83d5d-132">SRV_NETWORK_CONNECTION</span><span class="sxs-lookup"><span data-stu-id="83d5d-132">SRV_NETWORK_CONNECTION</span></span>|<span data-ttu-id="83d5d-133">현재 *srvproc* 연결에 사용된 네트워크 라이브러리 DLL에 전달된 연결 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-133">The connection string passed to the Net-Library DLL used for the current *srvproc* connection.</span></span>|  
|<span data-ttu-id="83d5d-134">SRV_PIPEHANDLE</span><span class="sxs-lookup"><span data-stu-id="83d5d-134">SRV_PIPEHANDLE</span></span>|<span data-ttu-id="83d5d-135">연결된 클라이언트의 파이프 핸들이 포함된 문자열입니다. 클라이언트가 명명된 파이프를 사용하지 않는 네트워크에 연결된 경우에는 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-135">A string containing the pipe handle of a connected client, or NULL if the client is connected on a network that does not use named pipes.</span></span> <span data-ttu-id="83d5d-136">이 핸들을 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows에서 유효한 파이프 핸들로 사용하려면 이 문자열을 정수로 변환하십시오.</span><span class="sxs-lookup"><span data-stu-id="83d5d-136">To use this handle as a valid pipe handle with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, convert this string to an integer.</span></span>|  
|<span data-ttu-id="83d5d-137">SRV_RMTSERVER</span><span class="sxs-lookup"><span data-stu-id="83d5d-137">SRV_RMTSERVER</span></span>|<span data-ttu-id="83d5d-138">클라이언트 프로세스가 로그인해 온 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-138">The server from which the client process is logged in.</span></span> <span data-ttu-id="83d5d-139">클라이언트에서 로그인한 경우에는 이 값이 빈 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-139">If the login is from a client, this value is an empty string.</span></span>|  
|<span data-ttu-id="83d5d-140">SRV_ROWSENT</span><span class="sxs-lookup"><span data-stu-id="83d5d-140">SRV_ROWSENT</span></span>|<span data-ttu-id="83d5d-141">현재 결과 집합에 대해 *srvproc*를 통해 이미 전송된 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-141">The number of rows already sent by *srvproc* for the current set of results.</span></span>|  
|<span data-ttu-id="83d5d-142">SRV_SPID</span><span class="sxs-lookup"><span data-stu-id="83d5d-142">SRV_SPID</span></span>|<span data-ttu-id="83d5d-143">*srvproc*의 서버 스레드 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-143">The server thread ID of the *srvproc*.</span></span> <span data-ttu-id="83d5d-144">확장 저장 프로시저의 경우 이 값은 **sys.sysprocesses**의 **kpid** 열과 같으며 시간이 지나면 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-144">For extended stored procedures, this value is the same as the **kpid** column of **sys.sysprocesses**, and it can change over time.</span></span>|  
|<span data-ttu-id="83d5d-145">SRV_SPROC_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="83d5d-145">SRV_SPROC_CODEPAGE</span></span>|<span data-ttu-id="83d5d-146">서버에서 멀티바이트 데이터를 해석하는 데 사용하는 코드 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-146">Codepage that the server uses to interpret multbyte data.</span></span>|  
|<span data-ttu-id="83d5d-147">SRV_STATUS</span><span class="sxs-lookup"><span data-stu-id="83d5d-147">SRV_STATUS</span></span>|<span data-ttu-id="83d5d-148">*srvproc*의 현재 상태로, 실행 중이거나 닫힌 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-148">The current status of *srvproc*: running or closed</span></span>|  
|<span data-ttu-id="83d5d-149">SRV_TYPE</span><span class="sxs-lookup"><span data-stu-id="83d5d-149">SRV_TYPE</span></span>|<span data-ttu-id="83d5d-150">*srvproc*의 연결 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-150">The connection type of *srvproc*.</span></span> <span data-ttu-id="83d5d-151">서버가 반환되면 *srvproc*가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 연결된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-151">If server is returned, *srvproc* is from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="83d5d-152">클라이언트가 반환되면 *srvproc*가 DB-Library 또는 ODBC 클라이언트에서 연결된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-152">If client is returned, *srvproc* is from a DB-Library or ODBC client.</span></span>|  
|<span data-ttu-id="83d5d-153">SRV_USER</span><span class="sxs-lookup"><span data-stu-id="83d5d-153">SRV_USER</span></span>|<span data-ttu-id="83d5d-154">연결 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-154">The user name of the connection.</span></span>|  
|||  
  
 <span data-ttu-id="83d5d-155">*길이가*</span><span class="sxs-lookup"><span data-stu-id="83d5d-155">*len*</span></span>  
 <span data-ttu-id="83d5d-156">반환된 *field* 값의 길이가 포함된 **int** 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-156">Is a pointer to an **int** variable that contains the length of the returned *field* value.</span></span> <span data-ttu-id="83d5d-157">*len*이 NULL이면 문자열 길이가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-157">If *len* is NULL, the length of the string is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="83d5d-158">반환</span><span class="sxs-lookup"><span data-stu-id="83d5d-158">Returns</span></span>  
 <span data-ttu-id="83d5d-159">SRV_PROC 구조에 지정된 필드에 대한 현재 값이 포함된 Null로 끝나는 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-159">A pointer to a null-terminated string containing the current value for the specified field in the SRV_PROC structure.</span></span> <span data-ttu-id="83d5d-160">필드가 비어 있으면 빈 문자열에 대한 올바른 포인터가 반환되고 *len*에 0이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-160">If the field is empty, a valid pointer to an empty string is returned and *len* contains 0.</span></span> <span data-ttu-id="83d5d-161">필드가 알 수 없는 필드이면 NULL이 반환되고 *len*에 -1 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-161">If the field is unknown, NULL is returned and *len* contains the value -1.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="83d5d-162">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83d5d-162">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="83d5d-163">보안 검토 및 테스트에 대한 자세한 내용은 [보안 개발자 센터(Security Developer Center)](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83d5d-163">For information about security review and testing, see the [Security Developer Center](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
