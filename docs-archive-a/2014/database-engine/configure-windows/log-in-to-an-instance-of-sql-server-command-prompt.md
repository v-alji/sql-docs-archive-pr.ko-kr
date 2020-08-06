---
title: SQL Server 인스턴스에 로그인(명령 프롬프트) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 32028a30786117f2cafa76150867a0e726b07cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646635"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a><span data-ttu-id="e3b60-102">SQL Server 인스턴스에 로그인(명령 프롬프트)</span><span class="sxs-lookup"><span data-stu-id="e3b60-102">Log In to an Instance of SQL Server (Command Prompt)</span></span>
  <span data-ttu-id="e3b60-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 연결을 테스트하고 **sqlcmd** 유틸리티를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3b60-103">This topic describes how to test connectivity to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the **sqlcmd** utility.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a><span data-ttu-id="e3b60-104">SQL Server의 기본 인스턴스에 로그인하려면</span><span class="sxs-lookup"><span data-stu-id="e3b60-104">To log in to the default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="e3b60-105">명령 프롬프트에서 다음 명령을 입력하여 Windows 인증을 통해 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e3b60-105">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a><span data-ttu-id="e3b60-106">SQL Server의 명명된 인스턴스에 로그인하려면</span><span class="sxs-lookup"><span data-stu-id="e3b60-106">To log in to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="e3b60-107">명령 프롬프트에서 다음 명령을 입력하여 Windows 인증을 통해 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e3b60-107">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e3b60-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3b60-108">See Also</span></span>  
 <span data-ttu-id="e3b60-109">[sqlcmd 유틸리티](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e3b60-109">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="e3b60-110">osql 유틸리티</span><span class="sxs-lookup"><span data-stu-id="e3b60-110">osql Utility</span></span>](../../tools/osql-utility.md)  
  
  
