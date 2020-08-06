---
title: SQL Server에서 확장 저장 프로시저 제거 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
ms.openlocfilehash: 284da815de073248669da032c06ddeeb68c697a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743256"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a><span data-ttu-id="d2a0d-102">SQL Server에서 확장 저장 프로시저 제거</span><span class="sxs-lookup"><span data-stu-id="d2a0d-102">Removing an Extended Stored Procedure from SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="d2a0d-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="d2a0d-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="d2a0d-104">사용자 정의 확장 저장 프로시저 DLL에서 각 확장 저장 프로시저 함수를 삭제 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자가 함수 이름 및 해당 함수가 상주 하는 DLL의 이름을 지정 하 여 **sp_dropextendedproc** 시스템 저장 프로시저를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2a0d-104">To drop each extended stored procedure function in a user-defined extended stored procedure DLL, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must run the **sp_dropextendedproc** system stored procedure, specifying the name of the function and the name of the DLL in which that function resides.</span></span> <span data-ttu-id="d2a0d-105">예를 들어이 명령은 xp_hello.dll 이라는 DLL에 있는 **xp_hello**함수를 제거 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d2a0d-105">For example, this command removes the function **xp_hello**, located in a DLL named xp_hello.dll, from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="d2a0d-106">부터 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **sp_dropextendedproc** 는 시스템 확장 저장 프로시저를 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2a0d-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** does not drop system extended stored procedures.</span></span> <span data-ttu-id="d2a0d-107">대신 시스템 관리자는 **공용** 역할에 대 한 확장 저장 프로시저에 대 한 EXECUTE 권한을 거부 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2a0d-107">Instead, the system administrator should deny EXECUTE permission on the extended stored procedure to the **public** role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a0d-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2a0d-108">See Also</span></span>  
 [<span data-ttu-id="d2a0d-109">sp_dropextendedproc&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d2a0d-109">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
