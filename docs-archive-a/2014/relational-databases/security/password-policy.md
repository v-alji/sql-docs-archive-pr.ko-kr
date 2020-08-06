---
title: 암호 정책 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- ALTER LOGIN statement
- passwords [SQL Server], policy enforcement
- logins [SQL Server], passwords
- CHECK_EXPIRATION option
- complex passwords [SQL Server]
- passwords [SQL Server], expiration
- manual bad password count resets
- MUST_CHANGE option
- expiration [SQL Server]
- expired password [SQL Server]
- symbols [SQL Server]
- NetValidatePasswordPolicy() API
- passwords [SQL Server]
- password policy [SQL Server]
- resetting bad password counts
- security [SQL Server], passwords
- CHECK_POLICY option
- passwords [SQL Server], symbols
- bad password counts
- passwords [SQL Server], complexity
- characters [SQL Server], password policies
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 902c46b4609a32139450843414a3c4d97b52fcf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647555"
---
# <a name="password-policy"></a><span data-ttu-id="e20b5-102">암호 정책</span><span class="sxs-lookup"><span data-stu-id="e20b5-102">Password Policy</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e20b5-103">에서는 Windows 암호 정책 메커니즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-103">can use Windows password policy mechanisms.</span></span> <span data-ttu-id="e20b5-104">암호 정책은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 로그인과 암호를 가진 포함된 데이터베이스 사용자에게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-104">The password policy applies to a login that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, and to a contained database user with password.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e20b5-105">에서는 Windows에서 사용되는 것과 동일한 복잡성 및 만료 정책을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]내부에 사용되는 암호에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-105">can apply the same complexity and expiration policies used in Windows to passwords used inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e20b5-106">이 기능은 `NetValidatePasswordPolicy` API 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-106">This functionality depends on the `NetValidatePasswordPolicy` API.</span></span>  
  
## <a name="password-complexity"></a><span data-ttu-id="e20b5-107">암호 복잡성</span><span class="sxs-lookup"><span data-stu-id="e20b5-107">Password Complexity</span></span>  
 <span data-ttu-id="e20b5-108">암호 복잡성 정책은 가능한 암호의 수를 늘려 문자 조합을 이용한 공격(brute force attacks)을 방지하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-108">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="e20b5-109">암호 복잡성 정책이 강제 적용된 경우 새 암호는 다음 지침을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-109">When password complexity policy is enforced, new passwords must meet the following guidelines:</span></span>  
  
-   <span data-ttu-id="e20b5-110">암호는 사용자의 계정 이름을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-110">The password does not contain the account name of the user.</span></span>  
  
-   <span data-ttu-id="e20b5-111">암호의 길이는 최소 8자 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-111">The password is at least eight characters long.</span></span>  
  
-   <span data-ttu-id="e20b5-112">암호는 다음 4가지 범주 중 세 범주의 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-112">The password contains characters from three of the following four categories:</span></span>  
  
    -   <span data-ttu-id="e20b5-113">라틴어 대문자(A - Z)</span><span class="sxs-lookup"><span data-stu-id="e20b5-113">Latin uppercase letters (A through Z)</span></span>  
  
    -   <span data-ttu-id="e20b5-114">라틴어 소문자(a - z)</span><span class="sxs-lookup"><span data-stu-id="e20b5-114">Latin lowercase letters (a through z)</span></span>  
  
    -   <span data-ttu-id="e20b5-115">기본 숫자 10가지(0 - 9)</span><span class="sxs-lookup"><span data-stu-id="e20b5-115">Base 10 digits (0 through 9)</span></span>  
  
    -   <span data-ttu-id="e20b5-116">느낌표(!), 달러 기호($), 숫자 기호(#) 또는 퍼센트(%)와 같은 영숫자 이외의 문자</span><span class="sxs-lookup"><span data-stu-id="e20b5-116">Non-alphanumeric characters such as: exclamation point (!), dollar sign ($), number sign (#), or percent (%).</span></span>  
  
 <span data-ttu-id="e20b5-117">암호 길이는 128자까지 가능하며</span><span class="sxs-lookup"><span data-stu-id="e20b5-117">Passwords can be up to 128 characters long.</span></span> <span data-ttu-id="e20b5-118">되도록 길고 복잡한 암호를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-118">You should use passwords that are as long and complex as possible.</span></span>  
  
## <a name="password-expiration"></a><span data-ttu-id="e20b5-119">암호 만료</span><span class="sxs-lookup"><span data-stu-id="e20b5-119">Password Expiration</span></span>  
 <span data-ttu-id="e20b5-120">암호 만료 정책을 사용하여 암호의 수명을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-120">Password expiration policies are used to manage the lifespan of a password.</span></span> <span data-ttu-id="e20b5-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 암호 만료 정책을 강제로 적용하면 사용자에게 기존 암호를 변경할 것과 암호가 만료되어 해당 계정을 사용할 수 없게 됨을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-121">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enforces password expiration policy, users are reminded to change old passwords, and accounts that have expired passwords are disabled.</span></span>  
  
## <a name="policy-enforcement"></a><span data-ttu-id="e20b5-122">정책 적용</span><span class="sxs-lookup"><span data-stu-id="e20b5-122">Policy Enforcement</span></span>  
 <span data-ttu-id="e20b5-123">암호 정책 적용은 각 SQL Server 로그인마다 별도로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-123">The enforcement of password policy can be configured separately for each SQL Server login.</span></span> <span data-ttu-id="e20b5-124">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) 을 사용하여 SQL Server 로그인의 암호 정책 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-124">Use [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy options of a SQL Server login.</span></span> <span data-ttu-id="e20b5-125">다음 규칙이 암호 정책 적용 구성에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-125">The following rules apply to the configuration of password policy enforcement:</span></span>  
  
-   <span data-ttu-id="e20b5-126">CHECK_POLICY가 ON으로 변경되면 다음 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-126">When CHECK_POLICY is changed to ON, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="e20b5-127">CHECK_EXPIRATION은 명시적으로 OFF로 설정되지 않은 한 마찬가지로 ON으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-127">CHECK_EXPIRATION is also set to ON unless it is explicitly set to OFF.</span></span>  
  
    -   <span data-ttu-id="e20b5-128">암호 기록이 현재 암호 해시 값으로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-128">The password history is initialized with the value of the current password hash.</span></span>  
  
    -   <span data-ttu-id="e20b5-129">**계정 잠금 기간**, **계정 잠금 임계값**및 **다음 시간 후 계정 잠금 수를 원래대로 설정** 도 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-129">**Account lockout duration**, **account lockout threshold**, and **reset account lockout counter after** are also enabled.</span></span>  
  
-   <span data-ttu-id="e20b5-130">CHECK_POLICY가 OFF로 변경되면 다음 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-130">When CHECK_POLICY is changed to OFF, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="e20b5-131">CHECK_EXPIRATION도 OFF로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-131">CHECK_EXPIRATION is also set to OFF.</span></span>  
  
    -   <span data-ttu-id="e20b5-132">암호 기록이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-132">The password history is cleared.</span></span>  
  
    -   <span data-ttu-id="e20b5-133">`lockout_time` 값이 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-133">The value of `lockout_time` is reset.</span></span>  
  
 <span data-ttu-id="e20b5-134">정책 옵션의 일부 조합은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-134">Some combinations of policy options are not supported.</span></span>  
  
-   <span data-ttu-id="e20b5-135">MUST_CHANGE를 지정한 경우에는 CHECK_EXPIRATION  및 CHECK_POLICY를 ON으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-135">If MUST_CHANGE is specified, CHECK_EXPIRATION and CHECK_POLICY must be set to ON.</span></span> <span data-ttu-id="e20b5-136">그렇지 않으면 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-136">Otherwise, the statement will fail.</span></span>  
  
-   <span data-ttu-id="e20b5-137">CHECK_POLICY를 OFF로 설정한 경우에는 CHECK_EXPIRATION을 ON으로 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-137">If CHECK_POLICY is set to OFF, CHECK_EXPIRATION cannot be set to ON.</span></span> <span data-ttu-id="e20b5-138">이 옵션 조합을 사용하면 ALTER LOGIN 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-138">An ALTER LOGIN statement that has this combination of options will fail.</span></span>  
  
 <span data-ttu-id="e20b5-139">CHECK_POLICY = ON을 설정하면 다음과 같은 암호가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-139">Setting CHECK_POLICY = ON will prevent the creation of passwords that are:</span></span>  
  
-   <span data-ttu-id="e20b5-140">Null 또는 빈 문자열 값의 암호</span><span class="sxs-lookup"><span data-stu-id="e20b5-140">Null or empty</span></span>  
  
-   <span data-ttu-id="e20b5-141">컴퓨터 또는 로그인 이름과 동일한 암호</span><span class="sxs-lookup"><span data-stu-id="e20b5-141">Same as name of computer or login</span></span>  
  
-   <span data-ttu-id="e20b5-142">"password", "admin", "administrator", "sa", "sysadmin" 중 하나</span><span class="sxs-lookup"><span data-stu-id="e20b5-142">Any of the following: "password", "admin", "administrator", "sa", "sysadmin"</span></span>  
  
 <span data-ttu-id="e20b5-143">보안 정책은 Windows에 설정하거나 도메인에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-143">The security policy might be set in Windows, or might be received from the domain.</span></span> <span data-ttu-id="e20b5-144">컴퓨터에 대한 암호 정책을 보려면 로컬 보안 정책 MMC 스냅인(**secpol.msc**)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e20b5-144">To view the password policy on the computer, use the Local Security Policy MMC snap-in (**secpol.msc**).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e20b5-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e20b5-145">Related Tasks</span></span>  
 [<span data-ttu-id="e20b5-146">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e20b5-146">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
 [<span data-ttu-id="e20b5-147">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e20b5-147">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
 [<span data-ttu-id="e20b5-148">CREATE USER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e20b5-148">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
 [<span data-ttu-id="e20b5-149">ALTER USER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e20b5-149">ALTER USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-user-transact-sql)  
  
 [<span data-ttu-id="e20b5-150">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="e20b5-150">Create a Login</span></span>](authentication-access/create-a-login.md)  
  
 [<span data-ttu-id="e20b5-151">데이터베이스 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="e20b5-151">Create a Database User</span></span>](authentication-access/create-a-database-user.md)  
  
## <a name="related-content"></a><span data-ttu-id="e20b5-152">관련 내용</span><span class="sxs-lookup"><span data-stu-id="e20b5-152">Related Content</span></span>  
 [<span data-ttu-id="e20b5-153">강력한 암호</span><span class="sxs-lookup"><span data-stu-id="e20b5-153">Strong Passwords</span></span>](strong-passwords.md)  
  
  
