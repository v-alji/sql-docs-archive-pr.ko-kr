---
title: SQL Server에 설치 된 확장 저장 프로시저 쿼리 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f44db9053ad18c3a6902a30aaab4f81610c5a8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648394"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a><span data-ttu-id="c8e7e-102">SQL Server에 설치된 확장 저장 프로시저 쿼리</span><span class="sxs-lookup"><span data-stu-id="c8e7e-102">Querying Extended Stored Procedures Installed in SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="c8e7e-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c8e7e-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="c8e7e-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 된 사용자는 **sp_helpextendedproc** 시스템 프로시저를 실행 하 여 현재 정의 된 확장 저장 프로시저와 각가 속한 DLL의 이름을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8e7e-104">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated user can display the currently defined extended stored procedures and the name of the DLL to which each belongs by running the **sp_helpextendedproc** system procedure.</span></span> <span data-ttu-id="c8e7e-105">예를 들어 다음 예에서는 **xp_hello** 속한 DLL을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8e7e-105">For example, the following example returns the DLL to which **xp_hello** belongs:</span></span>  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="c8e7e-106">확장 저장 프로시저를 지정 하지 않고 **sp_helpextendedproc** 를 실행 하면 모든 확장 저장 프로시저와 해당 dll이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8e7e-106">If **sp_helpextendedproc** is executed without specifying an extended stored procedure, all the extended stored procedures and their DLLs are displayed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c8e7e-107">로그인한 사용자가 소유하거나 권한이 있는 확장 저장 프로시저에 대해서만 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8e7e-107">Information will be returned for only those extended stored procedures that the logged in user owns or has permissions to.</span></span> <span data-ttu-id="c8e7e-108">**Sysadmin** 고정 서버 역할의 멤버와 **db_owner**, **db_securityadmin**및 **db_ddladmin** 고정 데이터베이스 역할의 멤버만이 모든 확장 저장 프로시저에 대 한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8e7e-108">Only members of the **sysadmin** fixed server role and the **db_owner**, **db_securityadmin**, and the **db_ddladmin** fixed database roles can view information for all extended stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e7e-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8e7e-109">See Also</span></span>  
 <span data-ttu-id="c8e7e-110">[Transact-sql&#41;sp_helpextendedproc &#40;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8e7e-110">[sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span></span>  
 <span data-ttu-id="c8e7e-111">[Transact-sql&#41;sp_addextendedproc &#40;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8e7e-111">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="c8e7e-112">sp_dropextendedproc&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c8e7e-112">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
