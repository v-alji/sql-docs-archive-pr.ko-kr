---
title: SqlContext 개체 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f036e274925f7b28b79f619f8e24b3e8804140
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734155"
---
# <a name="sqlcontext-object"></a><span data-ttu-id="372e0-102">SqlContext 개체</span><span class="sxs-lookup"><span data-stu-id="372e0-102">SqlContext Object</span></span>
  <span data-ttu-id="372e0-103">프로시저 또는 함수를 호출하거나, CLR(공용 언어 런타임) 사용자 정의 형식의 메서드를 호출하거나, 사용자의 동작이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 언어로 정의된 트리거를 발생시키면 서버에서 관리 코드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-103">You invoke managed code in the server when you call a procedure or function, when you call a method on a common language runtime (CLR) user-defined type, or when your action fires a trigger defined in any of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework languages.</span></span> <span data-ttu-id="372e0-104">이러한 코드 실행은 사용자 연결의 일부로 요청되므로 서버에서 실행되는 코드에서 호출자의 컨텍스트에 대한 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-104">Because execution of this code is requested as part of a user connection, access to the context of the caller from the code running in the server is required.</span></span> <span data-ttu-id="372e0-105">또한 특정 데이터 액세스 작업은 호출자의 컨텍스트에서 실행해야만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-105">In addition, certain data access operations may only be valid if run under the context of the caller.</span></span> <span data-ttu-id="372e0-106">예를 들어 트리거 작업에서 사용된 삽입되거나 삭제된 의사 테이블에 대한 액세스는 호출자의 컨텍스트에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-106">For example, access to inserted and deleted pseudo-tables used in trigger operations is only valid under the context of the caller.</span></span>  
  
 <span data-ttu-id="372e0-107">호출자의 컨텍스트는 `SqlContext` 개체에 추상화됩니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-107">The context of the caller is abstracted in a `SqlContext` object.</span></span> <span data-ttu-id="372e0-108">`SqlTriggerContext` 메서드 및 속성에 대한 자세한 내용은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK의 `Microsoft.SqlServer.Server.SqlTriggerContext` 클래스 참조 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="372e0-108">For more information about the `SqlTriggerContext` methods and properties, see the `Microsoft.SqlServer.Server.SqlTriggerContext` class reference documentation in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="372e0-109">`SqlContext`는 다음 구성 요소에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-109">`SqlContext` provides access to the following components:</span></span>  
  
-   <span data-ttu-id="372e0-110">`SqlPipe`: `SqlPipe` 개체는 결과가 클라이언트로 흐르는 "파이프"를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-110">`SqlPipe`: The `SqlPipe` object represents the "pipe" through which results flow to the client.</span></span> <span data-ttu-id="372e0-111">개체에 대 한 자세한 내용은 `SqlPipe` [SqlPipe 개체](sqlpipe-object.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="372e0-111">For more information about the `SqlPipe` object, see [SqlPipe Object](sqlpipe-object.md).</span></span>  
  
-   <span data-ttu-id="372e0-112">`SqlTriggerContext`: `SqlTriggerContext` 개체는 CLR 트리거 내 에서만 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-112">`SqlTriggerContext`: The `SqlTriggerContext` object can only be retrieved from within a CLR trigger.</span></span> <span data-ttu-id="372e0-113">이 개체는 트리거를 발생시킨 작업에 대한 정보와 업데이트된 열의 맵을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-113">It provides information about the operation that caused the trigger to fire and a map of the columns that were updated.</span></span> <span data-ttu-id="372e0-114">개체에 대 한 자세한 내용은 `SqlTriggerContext` [Sqltriggercontext 개체](sqltriggercontext-object.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="372e0-114">For more information about the `SqlTriggerContext` object, see [SqlTriggerContext Object](sqltriggercontext-object.md).</span></span>  
  
-   <span data-ttu-id="372e0-115">`IsAvailable`: `IsAvailable` 속성은 컨텍스트 가용성을 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-115">`IsAvailable`: The `IsAvailable` property is used to determine context availability.</span></span>  
  
-   <span data-ttu-id="372e0-116">`WindowsIdentity`: `WindowsIdentity` 속성은 호출자의 Windows id를 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-116">`WindowsIdentity`: The `WindowsIdentity` property is used to retrieve the Windows identity of the caller.</span></span>  
  
## <a name="determining-context-availability"></a><span data-ttu-id="372e0-117">컨텍스트 가용성 확인</span><span class="sxs-lookup"><span data-stu-id="372e0-117">Determining Context Availability</span></span>  
 <span data-ttu-id="372e0-118">`SqlContext` 클래스를 쿼리하면 현재 실행 중인 코드가 in-process로 실행 중인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-118">Query the `SqlContext` class to see if the currently executing code is running in-process.</span></span> <span data-ttu-id="372e0-119">이렇게 하려면 `IsAvailable` 개체의 `SqlContext` 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-119">To do this, check the `IsAvailable` property of the `SqlContext` object.</span></span> <span data-ttu-id="372e0-120">`IsAvailable` 속성은 읽기 전용이며, 호출 코드가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내에서 실행 중이고 다른 `True` 멤버에 액세스가 허용되면 `SqlContext`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-120">The `IsAvailable` property is read-only, and returns `True` if the calling code is running inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and if other `SqlContext` members can be accessed.</span></span> <span data-ttu-id="372e0-121">`IsAvailable` 속성이 `False`를 반환하는 경우 다른 모든 `SqlContext` 멤버를 사용하면 `InvalidOperationException`이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-121">If the `IsAvailable` property returns `False`, all the other `SqlContext` members throw an `InvalidOperationException`, if used.</span></span> <span data-ttu-id="372e0-122">`IsAvailable`이 `False`를 반환하는 경우 연결 문자열에 "context connection=true"가 있는 연결 개체를 열려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-122">If `IsAvailable` returns `False`, any attempt to open a connection object that has "context connection=true" in the connection string fails.</span></span>  
  
## <a name="retrieving-windows-identity"></a><span data-ttu-id="372e0-123">Windows ID 검색</span><span class="sxs-lookup"><span data-stu-id="372e0-123">Retrieving Windows Identity</span></span>  
 <span data-ttu-id="372e0-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내에서 실행되는 CLR 코드는 항상 프로세스 계정의 컨텍스트에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-124">CLR code executing inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is always invoked in the context of the process account.</span></span> <span data-ttu-id="372e0-125">코드에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 ID 대신 호출 사용자의 ID를 사용하여 특정 동작을 수행해야 하는 경우 `WindowsIdentity` 개체의 `SqlContext` 속성을 통해 가장 토큰을 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-125">If the code should perform certain actions using the identity of the calling user, instead of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process identity, then an impersonation token should be obtained through the `WindowsIdentity` property of the `SqlContext` object.</span></span> <span data-ttu-id="372e0-126">`WindowsIdentity` 속성은 호출자의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ID를 나타내는 `WindowsIdentity` 인스턴스를 반환하며, 클라이언트가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 인증된 경우에는 Null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-126">The `WindowsIdentity` property returns a `WindowsIdentity` instance representing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows identity of the caller, or null if the client was authenticated using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="372e0-127">`EXTERNAL_ACCESS` 또는 `UNSAFE` 권한으로 표시된 어셈블리만 이 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-127">Only assemblies marked with `EXTERNAL_ACCESS` or `UNSAFE` permissions can access this property.</span></span>  
  
 <span data-ttu-id="372e0-128">`WindowsIdentity` 개체를 얻으면 호출자는 클라이언트 계정을 가장하고 이를 대신해 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-128">After obtaining the `WindowsIdentity` object, callers can impersonate the client account and perform actions on their behalf.</span></span>  
  
 <span data-ttu-id="372e0-129">호출자 ID는 저장 프로시저 또는 함수 실행을 시작한 클라이언트가 Windows 인증을 사용하여 서버에 연결된 경우 `SqlContext.WindowsIdentity`를 통해서만 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-129">The identity of the caller is only available through `SqlContext.WindowsIdentity` if the client that initiated execution of the stored-procedure or function connected to the server using Windows Authentication.</span></span> <span data-ttu-id="372e0-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증이 사용된 경우 이 속성은 Null이며 코드는 호출자를 가장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-130">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication was used instead, this property is null and the code is unable to impersonate the caller.</span></span>  
  
### <a name="example"></a><span data-ttu-id="372e0-131">예제</span><span class="sxs-lookup"><span data-stu-id="372e0-131">Example</span></span>  
 <span data-ttu-id="372e0-132">다음 예에서는 호출 클라이언트의 Windows ID를 얻고 클라이언트를 가장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="372e0-132">The following example shows how to get the Windows identity of the calling client and impersonate the client.</span></span>  
  
 <span data-ttu-id="372e0-133">C#</span><span class="sxs-lookup"><span data-stu-id="372e0-133">C#</span></span>  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 <span data-ttu-id="372e0-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="372e0-134">Visual Basic</span></span>  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="372e0-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="372e0-135">See Also</span></span>  
 <span data-ttu-id="372e0-136">[SqlPipe 개체](sqlpipe-object.md) </span><span class="sxs-lookup"><span data-stu-id="372e0-136">[SqlPipe Object](sqlpipe-object.md) </span></span>  
 <span data-ttu-id="372e0-137">[SqlTriggerContext 개체](sqltriggercontext-object.md) </span><span class="sxs-lookup"><span data-stu-id="372e0-137">[SqlTriggerContext Object](sqltriggercontext-object.md) </span></span>  
 <span data-ttu-id="372e0-138">[CLR 트리거](../../database-engine/dev-guide/clr-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="372e0-138">[CLR Triggers](../../database-engine/dev-guide/clr-triggers.md) </span></span>  
 [<span data-ttu-id="372e0-139">ADO.NET에 대한 SQL Server In-Process 전용 확장</span><span class="sxs-lookup"><span data-stu-id="372e0-139">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
