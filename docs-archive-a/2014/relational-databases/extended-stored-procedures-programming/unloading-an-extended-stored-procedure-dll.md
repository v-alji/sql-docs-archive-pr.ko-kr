---
title: 확장 저장 프로시저 DLL 언로드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd4855390e95d949ab769d6567d6f106959dcde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638776"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a><span data-ttu-id="5ff1e-102">확장 저장 프로시저 DLL 언로드</span><span class="sxs-lookup"><span data-stu-id="5ff1e-102">Unloading an Extended Stored Procedure DLL</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="5ff1e-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ff1e-103">Use CLR Integration instead.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="5ff1e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dll의 함수 중 하나가 호출 되는 즉시 확장 저장 프로시저 DLL을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff1e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] loads an extended stored procedure DLL as soon as a call is made to one of the functions of the DLL.</span></span> <span data-ttu-id="5ff1e-105">서버가 종료되거나 시스템 관리자가 DBCC 문을 사용하여 언로드할 때까지 DLL은 로드된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ff1e-105">The DLL remains loaded until the server is shut down or until the system administrator uses the DBCC statement to unload it.</span></span> <span data-ttu-id="5ff1e-106">예를 들어이 명령은 **xp_hello.dll**를 언로드하고, 시스템 관리자가 서버를 종료 하지 않고이 파일의 최신 버전을 디렉터리에 복사할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff1e-106">For example, this command unloads the **xp_hello.dll**, allowing the system administrator to copy a newer version of this file to the directory without shutting down the server:</span></span>  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ff1e-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ff1e-107">See Also</span></span>  
 [<span data-ttu-id="5ff1e-108">DBCC dllname &#40;FREE&#41; &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="5ff1e-108">DBCC dllname &#40;FREE&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
