---
title: SQL Server에 확장 저장 프로시저 추가 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
author: rothja
ms.author: jroth
ms.openlocfilehash: 03ac8c2a0fa9ce77db59d50b3a7b9da42415e013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653394"
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a><span data-ttu-id="826a2-102">SQL Server에 확장 저장 프로시저 추가</span><span class="sxs-lookup"><span data-stu-id="826a2-102">Adding an Extended Stored Procedure to SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="826a2-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="826a2-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="826a2-104">확장 저장 프로시저 함수가 포함된 DLL은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 확장으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-104">A DLL that contains extended stored procedure functions acts as an extension to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="826a2-105">DLL을 설치 하려면 표준 dll 파일이 포함 된 디렉터리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (C:\Program FILES\MICROSOFT SQL Server\MSSQL12.0.\* )와 같은 디렉터리에 파일을 복사 합니다. \*기본적으로 x \MSSQL\Binn).</span><span class="sxs-lookup"><span data-stu-id="826a2-105">To install the DLL, copy the file to a directory, such as the one that contains the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files (C:\Program Files\Microsoft SQL Server\MSSQL12.0.*x*\MSSQL\Binn by default).</span></span>  
  
 <span data-ttu-id="826a2-106">확장 저장 프로시저 DLL을 서버에 복사한 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자가 DLL의 각 확장 저장 프로시저 함수를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-106">After the extended stored procedure DLL has been copied to the server, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must register to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] each extended stored procedure function in the DLL.</span></span> <span data-ttu-id="826a2-107">이 작업은 sp_addextendedproc 시스템 저장 프로시저를 사용하여 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-107">This is done using the sp_addextendedproc system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="826a2-108">시스템 관리자는 확장 저장 프로시저를 서버에 추가하고 다른 사용자에게 실행 권한을 부여하기 전에 각 확장 저장 프로시저를 철저히 검토하여 유해한 악성 코드가 포함되지는 않았는지를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-108">The system administrator should thoroughly review an extended stored procedure to ensure that it does not contain harmful or malicious code before adding it to the server and granting execute permissions to other users.</span></span>  <span data-ttu-id="826a2-109">모든 사용자 입력에 대해 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-109">Validate all user input.</span></span> <span data-ttu-id="826a2-110">유효성 검사를 수행하기 전에는 사용자 입력을 연결하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="826a2-110">Do not concatenate user input before validating it.</span></span> <span data-ttu-id="826a2-111">유효성 검사가 수행되지 않은 사용자 입력으로부터 생성된 명령은 실행하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="826a2-111">Never execute a command constructed from unvalidated user input.</span></span>  
  
 <span data-ttu-id="826a2-112">sp_addextendedproc의 첫 번째 매개 변수는 함수 이름을 지정하고 두 번째 매개 변수는 해당 함수가 있는 DLL의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-112">The first parameter of sp_addextendedproc specifies the name of the function, and the second parameter specifies the name of the DLL in which that function resides.</span></span> <span data-ttu-id="826a2-113">DLL의 전체 경로를 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-113">It is recommended that you specify the complete path of the DLL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="826a2-114">SQL Server 2005 이상으로 업그레이드하면 전체 경로에 등록되지 않은 기존 DLL은 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-114">Existing DLLs that were not registered with a complete path will not work after upgrading to SQL Server 2005 or later.</span></span> <span data-ttu-id="826a2-115">이 문제를 해결하려면 sp_dropextendedproc를 사용하여 DLL의 등록을 취소한 다음 전체 경로를 지정하여 sp_addextendedproc로 DLL을 다시 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-115">To correct the problem, use sp_dropextendedproc to unregister the DLL, and then reregister it with sp_addextendedproc, specifying the complete path.</span></span>  
  
 <span data-ttu-id="826a2-116">`sp_addextendedproc`에 지정된 함수 이름은 DLL의 함수 이름과 대/소문자를 포함하여 정확히 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-116">The name of the function specified in `sp_addextendedproc` must be exactly the same, including the case, as the function's name in the DLL.</span></span> <span data-ttu-id="826a2-117">예를 들어 다음 명령은 `xp_hello,`이라는 dll에 있는 `xp_hello.dll` 함수를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 저장 프로시저로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-117">For example, this command registers a function `xp_hello,` located in a dll named `xp_hello.dll`, as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure:</span></span>  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL12.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 <span data-ttu-id="826a2-118">`sp_addextendedproc`에 지정된 함수 이름이 DLL의 함수 이름과 정확히 일치하지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 새 이름이 등록되지만 해당 이름을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-118">If the name of the function specified in `sp_addextendedproc` does not exactly match the function name in the DLL, the new name will be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the name will not be usable.</span></span> <span data-ttu-id="826a2-119">예를 들어 `xp_Hello` 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 있는 확장 저장 프로시저로 등록 되더라도는를 사용 하 여 나중에 함수를 `xp_hello.dll` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 호출 하는 경우 DLL에서 함수를 찾을 수 없습니다 `xp_Hello` .</span><span class="sxs-lookup"><span data-stu-id="826a2-119">For example, although `xp_Hello` is registered as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure located in `xp_hello.dll`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to find the function in the DLL if you use `xp_Hello` to call the function later.</span></span>  
  
```  
--Register the function (xp_hello) with an initial upper case  
sp_addextendedproc 'xp_Hello', 'c:\xp_hello.dll';  
  
--Use the newly registered name to call the function  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
--This is the error message  
Server: Msg 17750, Level 16, State 1, Procedure xp_Hello, Line 1  
Could not load the DLL xp_hello.dll, or one of the DLLs it references. Reason: 127(The specified procedure could not be found.).  
```  
  
 <span data-ttu-id="826a2-120">`sp_addextendedproc`에 지정한 함수 이름이 DLL의 함수 이름과 정확히 일치하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 데이터 정렬에서 대/소문자를 구분하지 않는 경우 사용자는 이름의 대/소문자를 임의로 조합하여 확장 저장 프로시저를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-120">If the name of the function specified in `sp_addextendedproc` matches exactly the function name in the DLL, and the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-insensitive, the user can call the extended stored procedure using any combination of lower- and upper-case letters of the name.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will succeed in calling xp_hello  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HelLO @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
```  
  
 <span data-ttu-id="826a2-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 데이터 정렬에서 대/소문자를 구분하는 경우에는 프로시저가 DLL의 함수 이름 및 데이터 정렬과 정확히 일치하도록 등록되었더라도 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 대/소문자를 다르게 하여 프로시저를 호출하면 확장 저장 프로시저를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-121">When the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-sensitive, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to call the extended stored procedure -- even if it was registered with exactly the same name and collation as the function in the DLL -- if the procedure is called with a different case.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will result in an error  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
  
--This is the error  
Server: Msg 2812, Level 16, State 62, Line 1  
```  
  
 <span data-ttu-id="826a2-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 중지한 후 다시 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="826a2-122">It is not necessary to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826a2-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="826a2-123">See Also</span></span>  
 <span data-ttu-id="826a2-124">[Transact-sql&#41;sp_addextendedproc &#40;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="826a2-124">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="826a2-125">sp_dropextendedproc&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="826a2-125">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
