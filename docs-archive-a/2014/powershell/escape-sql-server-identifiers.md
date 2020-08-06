---
title: SQL Server 식별자 이스케이프 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1821187632aeeea0b7a18bf9c4d51d933e947d43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651055"
---
# <a name="escape-sql-server-identifiers"></a><span data-ttu-id="30085-102">SQL Server 식별자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="30085-102">Escape SQL Server Identifiers</span></span>
  <span data-ttu-id="30085-103">Windows PowerShell 역따옴표 이스케이프 문자(\`)를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구분 식별자에는 허용되고 Windows PowerShell 경로 이름에는 허용되지 않는 문자를 이스케이프 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30085-103">You can often use the Windows PowerShell back-tick escape character (\`) to escape characters that are allowed in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] delimited identifiers but not Windows PowerShell path names.</span></span> <span data-ttu-id="30085-104">하지만 이스케이프 처리되지 않는 문자도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30085-104">Some characters, however, cannot be escaped.</span></span> <span data-ttu-id="30085-105">예를 들어 Windows PowerShell에서 콜론 문자(:)는 이스케이프 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30085-105">For example, you cannot escape the colon character (:) in Windows PowerShell.</span></span> <span data-ttu-id="30085-106">해당 문자가 포함된 식별자는 인코딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30085-106">Identifiers with that character must be encoded.</span></span> <span data-ttu-id="30085-107">인코딩은 모든 문자에 대해 작동하므로 이스케이프 처리보다 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="30085-107">Encoding is more reliable than escaping because encoding works for all characters.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="30085-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="30085-108">Before You Begin</span></span>  
 <span data-ttu-id="30085-109">역따옴표 문자(\`) 키는 일반적으로 키보드 왼쪽 위에서 ESC 키 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30085-109">The back-tick character (\`) is usually on the key in the upper left of the keyboard, under the ESC key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="30085-110">예</span><span class="sxs-lookup"><span data-stu-id="30085-110">Examples</span></span>  
 <span data-ttu-id="30085-111">다음은 # 문자를 이스케이프 처리하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="30085-111">This is an example of escaping a # character:</span></span>  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 <span data-ttu-id="30085-112">다음은 (local)을 컴퓨터 이름으로 지정하는 경우 괄호를 이스케이프 처리하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="30085-112">This is an example of escaping the parenthesis when specifying (local) as a computer name:</span></span>  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a><span data-ttu-id="30085-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30085-113">See Also</span></span>  
 <span data-ttu-id="30085-114">[PowerShell에서 SQL Server 식별자](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="30085-114">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="30085-115">[SQL Server PowerShell 공급자](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="30085-115">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="30085-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="30085-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
