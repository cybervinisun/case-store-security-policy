# Information Security Policy — Case Store

**Version:** 1.2
**Effective date:** 2026-10-18
**Applicant / Owner:** Gleyson Araujo Oliveira, operating under the trade name ("nome fantasia") **Case Store**, a sole-proprietorship e-commerce business.
**Developer / Internal system:** **Sistema Intojados** is the name of the internal, proprietary order-management software built for and used exclusively by Case Store. It is not a separate company, vendor, or third-party developer — it is the software platform, developed for and operated solely by Gleyson Araujo Oliveira, through which this policy's technical controls are implemented and through which the TikTok Shop API integration is built.
**Scope:** This policy applies to all systems, devices, and data used by Gleyson Araujo Oliveira in the operation of Case Store's e-commerce business, including the Sistema Intojados order-management software and its integrations with third-party marketplace APIs (Mercado Livre, Shopee, Amazon, TikTok Shop).

**Relationship among these names:** Gleyson Araujo Oliveira is the sole owner and legal applicant for this integration. Case Store is the trade name under which this retail business operates and sells to customers. Sistema Intojados is the internal software system, developed for and used exclusively by this same business, that consolidates sales data and implements the API integrations and security controls described in this policy. All three names refer to the same single business and the same single responsible individual — there is no separate company, vendor, or third party involved.

## 1. Program overview and responsibility (Q1)

Case Store is a sole-operator retail business, legally represented by Gleyson Araujo Oliveira. There is no dedicated security team or multi-person organizational structure; all security responsibilities described in this policy are established, implemented, and maintained directly by Gleyson Araujo Oliveira, who also acts as the data protection contact (encarregado) under Brazil's LGPD.

This policy is reviewed and updated at least once per year, or sooner if there is a significant change to the business's systems, data handling practices, or applicable regulatory requirements (see Section 9).

## 2. Network segregation and protection (Q2)

- Device-to-device access (e.g., between the primary workstation and any other authorized device) is logically segmented through Tailscale, a WireGuard-based mesh VPN. Tailscale enforces a **default-deny access control list**: no device can reach another unless a rule explicitly authorizes that specific connection. This limits the blast radius of any single compromised device.
- The network's router/firewall has its built-in **Intrusion Prevention System (IPS)** enabled, providing perimeter-level monitoring and blocking of known attack patterns. This was confirmed active directly with the internet service provider's support team.
- There is no separate enterprise-grade network monitoring system, consistent with the scale of this business.

## 3. Endpoint protection (Q3)

- All devices used to access business systems run Windows Defender (built-in antivirus), which is kept continuously updated through automatic signature updates.
- Devices are covered individually, as there is a single operator and no fleet of company-managed endpoints beyond the primary workstation.

## 4. Authentication and workstation security (Q4)

- Devices used to access business systems require a password/PIN to unlock, and are configured to lock automatically after a period of inactivity.
- Multi-factor authentication (MFA) is enabled on accounts relevant to business operations, including e-mail and marketplace/developer partner portals, wherever the platform supports it.

## 5. Access control (Q5)

- As a sole-operator business, all systems and data are accessed by a single individual; there is no multi-person staff or contractor base requiring role-based access provisioning.
- API integrations follow the principle of least privilege: only the data scopes strictly necessary for order reconciliation and accounting are requested from each marketplace (for example, order and finance data, not product-catalog write access).
- Should additional personnel ever be granted access in the future, access will be provisioned on a least-privilege basis and reviewed periodically by the owner.

## 6. Data classification and encryption (Q6)

Case Store handles order-level data obtained through marketplace APIs: product, quantity, price, commission/fee, and buyer shipping information strictly as needed to fulfill and reconcile orders. This data is treated as sensitive and protected as follows:

- **At rest:** local databases that store order, product, and financial data are encrypted using SQLCipher with AES-256 (exceeding the AES-128 minimum baseline).
- **In transit:** all communication with marketplace APIs occurs over HTTPS/TLS (TLS 1.2 or higher, as negotiated by modern HTTPS clients).
- Only the minimum data necessary for order reconciliation and accounting is collected and retained; no additional personal data is collected beyond what each marketplace API provides for this purpose.

## 7. Incident response (Q7)

In the event of a suspected or confirmed security incident or data breach, the following process is followed:

1. **Containment:** the owner immediately restricts or revokes access (e.g., rotating credentials, disconnecting the affected device from the network) to stop further exposure.
2. **Assessment:** the owner assesses the scope of the incident — which systems, data, and third parties (sellers, platforms) may be affected.
3. **Notification:** any affected marketplace partners are notified directly and promptly, by e-mail or phone, with a description of what happened and what data may have been affected.
4. **Regulatory notification:** any legally required notification to a regulatory authority (e.g., under Brazil's LGPD) is made within the applicable legal timeframe.
5. **Review:** after resolution, the owner reviews what happened and updates this policy or practices if the incident reveals a gap.

Contact for security matters: viniciusnunes.qi@gmail.com

## 8. Vulnerability and threat management (Q8)

- Operating systems on all devices are kept current through automatic updates (Windows Update), which apply security patches as they are released.
- Antivirus signatures are updated automatically (see Section 3), providing ongoing protection against newly identified threats.
- The network router's firmware and IPS rule sets are maintained by the internet service provider as part of the managed equipment.
- As a sole-operator business, there is no formal scheduled vulnerability scanning program; patch and signature updates are applied automatically and checked periodically by the owner.

## 9. Data retention and deletion

- Data obtained through a marketplace API integration is retained only for as long as necessary for order reconciliation and accounting purposes.
- Upon request from a data subject, seller, or platform, or upon termination of the relevant API/contractual relationship, the corresponding data is deleted.

## 10. Policy review

This policy is reviewed and updated at least once per year, or sooner if there is a significant change to the business's systems, data handling practices, or applicable regulatory requirements. Last reviewed: 2026-10-18.

## 11. Contact

Questions about this policy may be directed to: viniciusnunes.qi@gmail.com

---

© 2026 Gleyson Araujo Oliveira (trade name: Case Store). All rights reserved. This document may not be reproduced or redistributed without permission.
