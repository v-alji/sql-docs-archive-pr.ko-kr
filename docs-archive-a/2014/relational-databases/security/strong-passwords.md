---
title: 강력한 암호 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5e878e0de5ee1f496dcc981182d42f5898838c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730304"
---
# <a name="strong-passwords"></a><span data-ttu-id="f91b6-102">강력한 암호</span><span class="sxs-lookup"><span data-stu-id="f91b6-102">Strong Passwords</span></span>
  <span data-ttu-id="f91b6-103">서버 보안 배포에서 암호는 가장 약한 링크가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-103">Passwords can be the weakest link in a server security deployment.</span></span> <span data-ttu-id="f91b6-104">암호를 선택할 때는 항상 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-104">You should always take great care when you select a password.</span></span> <span data-ttu-id="f91b6-105">강력한 암호의 특징은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-105">A strong password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="f91b6-106">길이가 적어도 8자 이상입니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-106">Is at least 8 characters long.</span></span>  
  
-   <span data-ttu-id="f91b6-107">암호는 문자, 숫자 및 기호의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-107">Combines letters, numbers, and symbol characters within the password.</span></span>  
  
-   <span data-ttu-id="f91b6-108">사전에 없는 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-108">Is not found in a dictionary.</span></span>  
  
-   <span data-ttu-id="f91b6-109">명령 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-109">Is not the name of a command.</span></span>  
  
-   <span data-ttu-id="f91b6-110">사람 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-110">Is not the name of a person.</span></span>  
  
-   <span data-ttu-id="f91b6-111">사용자 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-111">Is not the name of a user.</span></span>  
  
-   <span data-ttu-id="f91b6-112">컴퓨터 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-112">Is not the name of a computer.</span></span>  
  
-   <span data-ttu-id="f91b6-113">정기적으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-113">Is changed regularly.</span></span>  
  
-   <span data-ttu-id="f91b6-114">이전 암호와 전혀 다른 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-114">Is significantly different from previous passwords.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="f91b6-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 암호는 문자, 기호 및 숫자를 포함하여 최대 128자의 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passwords can contain up to 128 characters, including letters, symbols, and digits.</span></span> <span data-ttu-id="f91b6-116">로그인, 사용자 이름, 역할 및 암호가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 자주 사용되므로 특정 기호는 큰따옴표(") 또는 대괄호([ ])로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-116">Because logins, user names, roles, and passwords are frequently used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, certain symbols must be enclosed by double quotation marks (") or square brackets ([ ]).</span></span> <span data-ttu-id="f91b6-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] 로그인, 사용자, 역할 또는 암호가 다음에 해당할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문에 이러한 구분 기호를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f91b6-117">Use these delimiters in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, user, role, or password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="f91b6-118">공백 문자를 포함하거나 공백 문자로 시작하는 경우</span><span class="sxs-lookup"><span data-stu-id="f91b6-118">Contains or starts with a space character.</span></span>  
  
-   <span data-ttu-id="f91b6-119">$ 또는 \@ 문자로 시작하는 경우</span><span class="sxs-lookup"><span data-stu-id="f91b6-119">Starts with the $ or \@ character.</span></span>  
  
 <span data-ttu-id="f91b6-120">OLE DB 또는 ODBC 연결 문자열에서 사용할 경우 로그인 및 암호는 다음과 같은 문자 [] {}() , ; ?를 포함하지 말아야 함</span><span class="sxs-lookup"><span data-stu-id="f91b6-120">If used in an OLE DB or ODBC connection string, a login or password must not contain the following characters: [] {}() , ; ?</span></span> <span data-ttu-id="f91b6-121">\* !</span><span class="sxs-lookup"><span data-stu-id="f91b6-121">\* !</span></span> <span data-ttu-id="f91b6-122">\@.</span><span class="sxs-lookup"><span data-stu-id="f91b6-122">\@.</span></span> <span data-ttu-id="f91b6-123">문자를 포함할 수 없습니다. 이 문자는 연결을 시작하거나 연결 값을 구분하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f91b6-123">These characters are used to either initialize a connection or separate connection values.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="f91b6-124">관련 내용</span><span class="sxs-lookup"><span data-stu-id="f91b6-124">Related Content</span></span>  
 [<span data-ttu-id="f91b6-125">암호 정책</span><span class="sxs-lookup"><span data-stu-id="f91b6-125">Password Policy</span></span>](password-policy.md)  
  
  
